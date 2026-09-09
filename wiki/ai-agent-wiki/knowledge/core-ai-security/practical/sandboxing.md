---
tags: ["sandboxing", "ai-security", "guardrails", "red-team", "interview-prep"]
priority: high
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Sandboxing: Container Isolation, Network Egress Restrictions

> For agentic systems that execute code, fetch arbitrary URLs, or otherwise interact with the external world, sandboxing is the only defense against the LLM being steered (by prompt injection, by compromised retrieval, or by a malicious user) into destructive actions. The principle: assume the LLM 

For agentic systems that execute code, fetch arbitrary URLs, or otherwise interact with the external world, sandboxing is the only defense against the LLM being steered (by prompt injection, by compromised retrieval, or by a malicious user) into destructive actions. The principle: assume the LLM is malicious, and put it in a cage.

#### 5.1 Execution sandbox taxonomy

Three classes of sandbox are commonly used, in increasing order of isolation strength:

**Process-level (lightest).** Run untrusted code in a subprocess with `seccomp` to restrict syscalls, `prctl` to drop capabilities, and resource limits (`rlimit`) to cap CPU, memory, and file descriptors. Sub-100ms startup. Suitable for executing short, trusted code snippets (e.g., a small Python expression) where the worst-case damage is a process crash. Not suitable for code that may try to exfiltrate data — the subprocess has the network namespace of its host.

**Container-level (medium).** Run untrusted code in a Docker / containerd / Podman container with a minimal base image, dropped Linux capabilities, read-only root filesystem (except a scratch dir), AppArmor or SELinux profile, seccomp filter, and no new privileges. Sub-second startup. The container shares the host kernel, so kernel-level escape vulnerabilities (historically common) are a real risk. Use for short-lived workloads (a few seconds to a few minutes) where the code is *somewhat* trusted.

**MicroVM-level (heaviest).** Run untrusted code in a hardware-virtualized microVM:
- **Firecracker** (AWS): sub-125ms boot, KVM-based, designed for Lambda and similar serverless workloads. Used in production by AWS, Fly.io, and others. Includes a minimal guest kernel and a virtio-block device. Memory overhead is ~5 MiB.
- **gVisor** (Google): user-space kernel that intercepts and limits syscalls; the guest application can only interact with the host through gVisor's carefully-audited syscall filter. ~1-2s boot. Used in production by Google Cloud Run and App Engine. Stronger than a normal container because the host kernel is shielded from the guest.
- **Kata Containers**: OCI-compatible runtime that runs each container in its own QEMU/KVM microVM. Drop-in for containerd, with VM-level isolation but slower boot than Firecracker.
- **Wasmtime / WasmEdge**: WebAssembly runtime with capability-based security. Sub-millisecond startup. Suitable for sandboxing untrusted *logic* but not full code; the Wasm module cannot make syscalls it wasn't given.

The right choice depends on the threat model: a code-execution agent processing untrusted Python should run in a microVM; a content-retrieval agent that doesn't execute user-supplied code can use a lighter container.

#### 5.2 Network egress restrictions

The single most important sandboxing rule: **no outbound network by default**. Then, on top:

- **Egress allowlist.** A list of hostnames or CIDR ranges the agent is allowed to reach. Everything else is dropped at the firewall. DNS is sinkholed (e.g., to `0.0.0.0` or a logging resolver) for any non-allowlisted domain.
- **TLS interception.** For agent traffic that *is* allowlisted, the egress proxy intercepts the TLS connection and inspects the SNI / certificate; the proxy can be configured to refuse connections to look-alike domains (`g00gle.com` vs. `google.com`).
- **No loopback.** Block connections to `127.0.0.1`, the host's internal services, and the link-local `169.254.0.0/16` range. This prevents the agent from probing host services.
- **Connection limits.** Cap the number of outbound connections per session (e.g., 100) and the total bytes transferred (e.g., 50 MB). This limits exfiltration.
- **Time-of-day rules.** For high-stakes systems, allow egress only during business hours. Reduces the chance of an exfiltration attack succeeding undetected overnight.

The agent *cannot* extend its own allowlist. If a new endpoint is needed, a human must edit the configuration and redeploy.

#### 5.3 Filesystem, secrets, resources

**Filesystem read-only by default.** The root filesystem is read-only. A scratch `/tmp` (or a per-task tmpfs) is writable and is destroyed when the sandbox is destroyed. Outputs are pulled out via a controlled channel (the orchestrator reads `/tmp/results.json` after the agent finishes), not by the agent.

**No persistent credentials.** API keys for downstream services are issued *per session* with short TTLs (1 hour) and per-action scopes. The credentials are passed as environment variables to the sandbox at start; they are not on disk. The credentials are revoked when the sandbox is destroyed. No long-lived secrets ever live in the sandbox image.

**Resource ceilings.** CPU, memory, wall-clock, and disk quotas are enforced by the container/microVM runtime. A runaway agent is OOM-killed. Wall-clock is critical for code-execution agents — an infinite loop without a wall-clock limit will hang the worker.

**Per-task identity.** Each sandbox has a unique non-privileged user; a vulnerability in one sandbox cannot impersonate another.

#### 5.4 Browser sandboxing (for web-browsing agents)

Web-browsing agents face the XSS-into-prompt channel: an attacker hosts a page with hidden instructions for the LLM. The defenses:

- **Render in a stripped text-only intermediate.** Use a headless browser to fetch and render, but extract only plain text; never let raw HTML, JavaScript, or CSS reach the LLM.
- **Use a remote browser service.** Browserbase, Steel.dev, Anchor Browser, or self-hosted remote Chrome provide an isolated browsing environment with per-session cookies and no local file access. The agent interacts with the browser via CDP; the agent's process never directly holds the cookies.
- **Per-domain sandboxing.** Each fetched page runs in a separate iframe sandbox with no script, no cookies, no local storage, and no network access. The host page never sees the fetched content.
- **Visual screenshot analysis.** When vision is needed, render to a screenshot, send the screenshot to a separate vision model, and discard the original HTML.

#### 5.5 The kill switch

A sandboxed agent must be killable in seconds from the operator console. The kill switch:

- Sends SIGKILL to the sandbox process immediately.
- Revokes the per-session credentials at the identity provider.
- Flushes the in-flight tool calls.
- Writes a final entry to the audit log.
- Pages the on-call if the kill was triggered automatically (anomalous activity).

Without a kill switch, an incident becomes a hostage situation where you must wait for the agent to finish a 30-minute task before you can stop it.

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
