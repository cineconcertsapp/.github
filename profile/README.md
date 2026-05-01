# CineConcerts

Live cinematic concert experiences worldwide.

## Shared infrastructure

This repository hosts org-wide GitHub configuration:

- **Reusable workflows** — `/.github/workflows/`
- **Workflow templates** — `/.github/workflow-templates/` (shown when creating a new workflow in any org repo)

### opencode AI agent

Any repo in this org can opt in to the opencode AI agent by adding `.github/workflows/opencode.yml`:

```yaml
name: opencode

on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]

jobs:
  opencode:
    uses: cineconcertsapp/.github/.github/workflows/opencode-reusable.yml@main
    secrets:
      OPENCODE_API_KEY: ${{ secrets.OPENCODE_API_KEY }}
```

Once added, comment `/oc <prompt>` on any issue or PR review to invoke it.
The `OPENCODE_API_KEY` is provided as an org-level secret.
