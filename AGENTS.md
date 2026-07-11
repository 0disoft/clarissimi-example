# AGENTS.md

## Scope

This public repository is a minimal consumer example for `0disoft/clarissimi`.

## Rules

- Keep every fixture explicitly synthetic.
- Do not commit credentials, tokens, private data, production data, or generated workflow artifacts.
- Keep the default workflow read-only.
- Keep write-mode examples manual-only with least-privilege permissions.
- Pin Clarissimi to the supported `v0` Action channel or an immutable version tag, never `main`.
- Validate workflow YAML with `actionlint` and `yq` before push.
- Preserve unrelated user changes.

## Final Reports

List changed files, executed and skipped validation, workflow run URLs, repository visibility,
permissions changes, and remaining risk.
