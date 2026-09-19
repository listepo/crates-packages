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

Pushing to `main` runs CI (fmt, clippy, unit tests) plus a
`cargo publish --dry-run` check. Publishing to crates.io happens only when a
**non-draft** GitHub Release is published (`release: types: [published]` with
a `draft == false` guard). Creating a draft release does nothing; publishing
the release publishes the crates.
