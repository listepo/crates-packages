# crates-packages

[![ci](https://github.com/listepo/crates-packages/actions/workflows/ci.yml/badge.svg)](https://github.com/listepo/crates-packages/actions/workflows/ci.yml)

Small, focused Rust crates shared by `ketch` and `rtok`.

| Crate | What it does |
| --- | --- |
| [`file-backup`](file-backup) | Copy a file to `<name>.bak-<unix-seconds>` beside it before replacing it |

## Commands

```bash
cargo test --workspace --locked
cargo clippy --workspace --all-targets --locked -- -D warnings
cargo fmt --all -- --check
```

## Release

- Pushing to `main` runs CI (commits lint on PRs, fmt, clippy, unit tests,
  publish dry-run).
- `release-plz` keeps one release pull request up to date from conventional
  commits; merging it bumps the version and the changelog.
- Merging a version bump triggers `release.yml`: it re-runs the gate,
  publishes to crates.io, then creates the GitHub release as a draft and
  publishes it — publishing the release is what creates the
  `file-backup-v<version>` tag. A failed build leaves main untagged.
- `gh workflow run release.yml -f bump=patch|minor|major` opens a bump PR
  without release-plz.

Secrets: `CARGO_REGISTRY_TOKEN` (crates.io API token) and
`RELEASE_PLZ_TOKEN` (a PAT that can trigger workflows, see
https://release-plz.dev/docs/github/token).
