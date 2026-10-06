# Polyline

Encode and decode lists of coordinates as compact ASCII strings. Implements Google's Encoded Polyline Algorithm Format, encode and decode, precision 1–10.

The spec and conformance cases for Polyline. Each language port lives in its own repo and is tested against the same cases.

> **Coordinate order:** the API uses `(lon, lat)`; the encoded string stores latitude first. See `spec/SPEC.md`.

## Ports

| Language | Repo | Package | Spec pinned | Conformance | Status |
|---|---|---|---|---|---|
| Zig | `Xenoglyphiq/polyline-zig` | `polyline` | – | – | planned |
| Julia | `Xenoglyphiq/EncodedPolyline.jl` | `EncodedPolyline` | – | – | planned |
| Nim | `Xenoglyphiq/polyline-nim` | `polyline` | – | – | planned |

Install instructions and examples are in each port's repo.

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
