# semantic-basic-template

This template repository publishes releases from `main`. Stable template tags
drive automatic propagation to consumers.

The shared `.github/workflows/semantic.yml` validates pull requests targeting
`main`, optional `rc`, and legacy `release`, and runs semantic-release on pushes
to those branches. 
For consumers that need a release-created push or tag to trigger downstream
GitHub Actions workflows, configure `SEMANTIC_RELEASE_TOKEN` with a suitable
personal access token and permissions. The workflow falls back to
`GITHUB_TOKEN`, but events caused by that token generally do not trigger
other workflows. Do not require a PAT where downstream workflow triggering
is unnecessary.

The legacy `force-release-pr.yml` workflow was removed; automatic PR title
and description generation for `main` → `release` is no longer provided.
