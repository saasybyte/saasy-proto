# saasy-proto

## Conventions
- **Never change field numbers** once published — clients decode by number, not name.
- **Use `reserved`** when removing fields — prevents accidental reuse of field numbers and names.
- **Enum first value must be 0** (`UNSPECIFIED`) — proto3 requirement, also catches unset states.
- **Use `oneof`** for optional scalars (e.g., `uint32`, `bool`, `enum`) — gives correct `Option<T>` in Rust via `prost`.
- **Field numbers 1–15** use 1 byte on the wire — prefer for high-frequency fields.
- **No build tooling here** — consuming repos generate code from these protos.

## Service Boundaries
- **Consumed by all SaasyByte services**: saasy-signal, saasy-sfu, saasy-core, saasy-edge, saasy-orchestrator, saasy-media-engine, saasy-web.
- **Does not own**: code generation (consuming repos), runtime behavior, auth, media, or AI inference.
