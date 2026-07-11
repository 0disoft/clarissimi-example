# Clarissimi Example

[![Clarissimi dry-run example](https://github.com/0disoft/clarissimi-example/actions/workflows/clarissimi-dry-run.yml/badge.svg)](https://github.com/0disoft/clarissimi-example/actions/workflows/clarissimi-dry-run.yml)

Public, synthetic consumer example for [`0disoft/clarissimi`](https://github.com/0disoft/clarissimi).
It shows the two boundaries most repositories need:

- a read-only dry run that can execute on every change;
- a manual recognition proposal that opens a pull request instead of mutating `main`.

No provider token or other secret is required. Both workflows use Clarissimi's deterministic fake
provider and the maintained `0disoft/clarissimi@v0` Action channel.

## Read-Only Dry Run

The default workflow grants only `contents: read` and validates the Action outputs plus the
sanitized JSON summary artifact.

```yaml
permissions:
  contents: read

steps:
  - uses: actions/checkout@v7.0.0
  - uses: 0disoft/clarissimi@v0
    with:
      mode: dry-run
      github-fixture: fixtures/github-merged-pr-approved.json
```

## Recognition Proposal

The write-mode example is manual-only. It grants `contents: write` and `pull-requests: write`,
creates a unique synthetic merged-PR fixture, and asks Clarissimi to open a normal recognition pull
request. `main` changes only after a maintainer reviews and merges that pull request.

The workflow sets `markdown-summary: table`, so merged output includes a compact contributor count
table followed by the evidence-linked recognition details. Use a new positive `source-id` for each
manual run.

## Safety Boundary

- All evidence is synthetic and marked as such.
- No workflow executes untrusted pull-request code.
- The default workflow cannot write repository contents.
- The proposal workflow runs only through `workflow_dispatch`.
- Clarissimi's moving `v0` alias is independently verified against its immutable release in the
  upstream repository. Pin an immutable patch tag when exact dependency reproducibility is needed.
