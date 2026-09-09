---
tags: ["strix", "ci-cd", "github-actions", "security-gate", "red-team", "ai-security"]
related: ["ai-agent-wiki/18-strix", "ai-agent-wiki/strix/_index", "ai-agent-wiki/core-ai-security/essential/red-team-methodology", "ai-agent-wiki/core-ai-security/practical/implementation-playbook"]
created: 2026-09-08
---

# Strix — Running in CI

> **Strix's headless mode (`strix -n --target ./ --scan-mode quick`) is designed for CI** — wire it into a security-gate job that runs on every PR touching an AI surface, block merge on findings, and feed the SARIF output into the existing GitHub code-scanning tab.

## GitHub Actions skeleton

```yaml
name: strix-pentest
on:
  pull_request:
    paths:
      - "app/**"
      - "api/**"
      - "mcp-servers/**"
jobs:
  strix:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run Strix headless
        env:
          STRIX_LLM_API_KEY: ${{ secrets.STRIX_LLM_API_KEY }}
        run: |
          npx strix --target ./app --scan-mode quick                      --output-format sarif                      --output-path strix.sarif                      --fail-on high
      - name: Upload SARIF
        if: always()
        uses: github/codeql-action/upload-sarif@v3
        with:
          sarif_file: strix.sarif
```

## What this gets you

- **PR-level coverage** of the OWASP App Top 10 (A01–A10) on every change to an AI surface
- **SARIF output** flows into the GitHub code-scanning tab alongside CodeQL / Semgrep / Dependabot findings
- **`--fail-on high`** blocks the merge if Strix finds a high-severity issue (configurable; `medium` for stricter projects)
- **Headless + quick mode** keeps the run under ~5 min and the LLM cost under ~$1 per PR (per Strix's published cost benchmarks)

## Where to put it in the pipeline

- **On every PR to `main`** touching an AI-touching path: yes, always
- **On every nightly run** against a staging environment: yes, with `--scan-mode full` instead of `quick`
- **On release tags**: yes, full-mode + manual review of medium findings

## Cost and time budget

Per the Strix README's cost benchmarks (v1.6.2, 2026-09-05):

| Scan mode | Wall-clock | LLM cost | When to run |
|---|---|---|---|
| `quick` | 3-5 min | ~$0.50–1.00 | Per PR |
| `full` | 20-45 min | ~$8–17 | Nightly / release |
| `cloud` | external | per-scan pricing | When self-hosting LLM is infeasible |

## Configuration hygiene

- **Spend-capped API key**: scope the LLM key to a hard daily/monthly cap. Strix can otherwise generate cost blowouts from a prompt-loop bug.
- **Source-not-URL**: feed Strix the local checkout, not a deployed URL. Faster, cheaper, and avoids accidentally testing production.
- **Scoped CI runs**: only run on changes that touch the AI surface. Don't run on docs-only PRs.
- **Time-box**: pass `--max-runtime 600` to hard-cap any one scan. Strix's per-run worst case is bounded; this is a belt-and-suspenders cap.

## When Strix should NOT be in CI

- **First-time setup on a legacy app**: Strix will find *thousands* of issues. Run manually first, fix the high/critical, then wire into CI.
- **App has no testable staging environment**: Strix's `$59/pentest` Quick-Audit tier is more cost-effective than CI for a one-shot.
- **Lacking LLM budget**: without an API key, Strix is a no-op. If you cannot afford the LLM cost, fall back to manual pentests and a static scanner.

## Related

- [[ai-agent-wiki/18-strix|Strix (18)]] — canonical product page
- [[ai-agent-wiki/strix/_index|Strix sub-hub]]
- [[ai-agent-wiki/core-ai-security/essential/red-team-methodology|Red-Teaming Methodology]]
- [[ai-agent-wiki/core-ai-security/practical/implementation-playbook|Implementation Playbook]]
