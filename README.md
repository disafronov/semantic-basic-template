# semantic-basic-template

This template repository publishes stable releases directly from `main`.
It has no RC cycle or `release` branch: stable template tags drive automatic
propagation to consumers.

The standalone `.releaserc.cjs` controls releases of this template itself,
using `branches: ["main"]`. It is excluded from synchronization so consumer
repositories retain their own release policies.

The shared `.github/workflows/semantic.yml` validates pull requests targeting
`main`, optional `rc`, and legacy `release`, and runs semantic-release on pushes
to those branches. **A workflow trigger does not enable a release branch:**
consumers must configure their own `.releaserc` to publish from `rc` or
`release`. The template itself publishes stable releases only from `main`.

For consumers that need a release-created push or tag to trigger downstream
GitHub Actions workflows, configure `SEMANTIC_RELEASE_TOKEN` with a suitable
personal access token and permissions. The workflow falls back to
`GITHUB_TOKEN`, but events caused by that token generally do not trigger
other workflows. Do not require a PAT where downstream workflow triggering
is unnecessary.

The legacy `force-release-pr.yml` workflow was removed; automatic PR title
and description generation for `main` → `release` is no longer provided.
