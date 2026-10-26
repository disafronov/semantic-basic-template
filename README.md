# semantic-basic-template

This template repository publishes stable releases directly from `main`.
It has no RC cycle or `release` branch: stable template tags drive automatic
propagation to consumers.

The standalone `.releaserc.cjs` configures releases of this template itself.
It retains the shared release rules, plugins and Git committer sign-off while
using `branches: ["main"]`. It must stay outside the synchronizer's
`include.list` so it does not override consumers' own release policies.

The shared `semantic.yml` workflow supports both `main` and `release` for
consumer projects; each repository's release configuration selects its policy.
