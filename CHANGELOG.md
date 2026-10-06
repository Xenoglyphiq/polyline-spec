# Changelog

Spec releases. Ports vendor a tagged release into `.spec/`; the version here is `spec_version` in `spec/capability.yaml`.

## 0.1.1 — 2026-10-05

No behavior change; conformance cases are identical (only their `spec_version` stamp changed).

- `bench/README.md`: the shared benchmark method every port follows.
- `bench/rust/`: the performance reference, the Rust `polyline` crate pinned at `=0.11.0`.

## 0.1.0 — 2026-10-05

First release: `encode` and `decode`, 7 error codes, 2 limits, 44 conformance cases, decisions D-001 to D-004.
