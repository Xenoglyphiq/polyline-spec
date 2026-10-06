# Polyline

Encode and decode lists of coordinates as compact ASCII strings. Implements Google's Encoded Polyline Algorithm Format, encode and decode, precision 1–10.

The spec and conformance cases for Polyline. Each language port lives in its own repo and is tested against the same cases.

> **Coordinate order:** the API uses `(lon, lat)`; the encoded string stores latitude first. See `spec/SPEC.md`.

## Ports

| Language | Repo | Package | Spec pinned | Conformance | Status |
|---|---|---|---|---|---|
| Zig | [`Xenoglyphiq/polyline-zig`](https://github.com/Xenoglyphiq/polyline-zig) | `polyline` | 0.1.1 | core ✓ full ✓ (44/44) | **released v0.1.0**: git tag; tagged `zig-package` for zigistry to index |
| Julia | [`Xenoglyphiq/EncodedPolyline.jl`](https://github.com/Xenoglyphiq/EncodedPolyline.jl) | `EncodedPolyline` | 0.1.1 | core ✓ full ✓ (44/44) | feature-complete; first release pending |
| Nim | [`Xenoglyphiq/polyline-nim`](https://github.com/Xenoglyphiq/polyline-nim) | `polyline` | 0.1.1 | core ✓ full ✓ (44/44) | **released v0.1.0**: git tag; Nimble directory listing in review |

All three ports are within 2× of the Rust reference on both operations (`bench/README.md`). Install instructions and examples are in each port's repo.

## What's here

| Path | What |
|---|---|
| `spec/SPEC.md` | Behavior spec |
| `spec/capability.yaml` | Machine-readable contract: operations, errors, limits |
| `conformance/` | Test cases every port must pass; regenerate with `uv run conformance/generate/generate.py` |
| `bench/` | Shared benchmark inputs |
| `.kit/` | Shared conventions, schemas and validator (vendored) |
| `CONTRIBUTING.md` | How changes to the spec are made |
| `DECISIONS.md` | Why the spec is the way it is |

## Contributing

See `CONTRIBUTING.md`.

## License

MIT OR Apache-2.0
