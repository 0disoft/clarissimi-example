# Validation

## Stable Checks

- `check`: `git diff --check`
- `workflow-lint`: `actionlint`
- `yaml-parse`: parse every `.github/workflows/*.yml` with `yq`
- `fixture-parse`: parse every `fixtures/*.json` with `jq`
- `smoke`: run `Clarissimi dry-run example` on GitHub Actions
- `write-smoke`: manually run `Clarissimi recognition proposal`, inspect its pull request, and
  merge only synthetic output

No package build, database migration, formatter, or dependency installation is required.
