# actions

Reusable GitHub Actions for OpenShock repos: composite actions (one per subfolder) plus a reusable workflow under `.github/workflows/`.

## Composite actions

| Action | Purpose |
|---|---|
| [`release-download`](./release-download) | Download (and optionally extract) an asset from the latest GitHub release of a repo |
| [`repository-dispatch`](./repository-dispatch) | Send a `repository_dispatch` event to another repo |
| [`find-latest-tag`](./find-latest-tag) | Find the latest git tag matching a regex, sorted by semver |
| [`nsis-build`](./nsis-build) | Install NSIS and compile an installer script (Windows runners only) |
| [`open-pr-from-diff`](./open-pr-from-diff) | Commit any working-tree changes to a branch, push it, and open (or reuse) a PR |
| [`auto-commit`](./auto-commit) | Commit any working-tree changes and push to the current branch; no-op if there's nothing to commit |
| [`publish-tag`](./publish-tag) | Push the current commit and a tag together (e.g. the `tag` output from `OpenShock/release-tool`); no-op if the tag is empty |

Reference these as `uses: OpenShock/actions/<name>@<ref>`.

## Reusable workflows

| Workflow | Purpose |
|---|---|
| [`.github/workflows/pr-check-comment.yml`](./.github/workflows/pr-check-comment.yml) | Downloads a `release-check` verdict artifact from a `workflow_run` and posts/updates/removes a sticky PR comment based on it |

Reference this as `uses: OpenShock/actions/.github/workflows/pr-check-comment.yml@<ref>` from a job.

`OpenShock/release-tool` is intentionally not here. It's a separate Go program with its own build/release lifecycle, not a thin YAML wrapper, and it now handles its own release-mode git prep (rebase + tag fetch) internally.
