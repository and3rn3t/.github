# .github — shared workflows & defaults

Special repository: reusable GitHub Actions workflows, workflow templates, and default community health files for all `and3rn3t` repos.

## Reusable workflows

Call from any repo's workflow:

```yaml
jobs:
  quality:
    uses: and3rn3t/.github/.github/workflows/reusable-node-verify.yml@main
    with:
      command: pnpm lint && pnpm type-check && pnpm test && pnpm build
      package-manager: pnpm
```

| Workflow | Purpose | Key inputs |
|---|---|---|
| `reusable-node-verify.yml` | Checkout → Node setup (from `.nvmrc`) → install → run command | `command` (required), `package-manager` (npm/pnpm), artifact options |
| `reusable-python-test.yml` | pytest across a Python version matrix | `python-versions`, `install-command`, `test-command` |
| `reusable-codeql.yml` | CodeQL security analysis | `languages` (required, JSON array) |
| `reusable-dependency-review.yml` | PR dependency review | `fail-on-severity` (default critical) |
| `reusable-playwright-e2e.yml` | Playwright e2e + always-uploaded report | `command`, `package-manager`, `browsers`, `report-path` |

## Workflow templates

`workflow-templates/` adds "and3rn3t Node CI" and "and3rn3t Python CI" to the New Workflow chooser in all repos.

## Defaults

`SECURITY.md` here applies to any repo that doesn't define its own. `.github/release-drafter.yml` is the default Release Drafter config for all repos.

## Conventions

Repos consuming these workflows follow the standards in [`ai-template-repo`](https://github.com/and3rn3t/ai-template-repo): AGENTS.md single-source instructions, Renovate, conventional commits, Node 24.

> This repo must be **public** for reusable workflows and templates to work across repos.
