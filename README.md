# saasy-proto

Canonical Proto3 schemas for [SaasyByte](https://github.com/saasybyte/saasybyte), an open-source real-time AI voice platform.

Every message that crosses a service boundary is defined here: signaling envelopes, SFU media operations, engine control, and backend contracts. Consuming repositories vendor this repo (as a git submodule or via generated packages) and run their own code generation; this repository intentionally contains no build tooling.

## Consumers

- [saasy-proto-rust](https://github.com/saasybyte/saasy-proto-rust) generates types for the Rust services (signal, sfu, orchestrator).
- [saasy-proto-ts](https://github.com/saasybyte/saasy-proto-ts) generates types for the web client.
- saasy-core, saasy-edge, and saasy-media-engine include this repo as a submodule and generate in-tree.

## Conventions

- Never change a published field number; use `reserved` when removing fields.
- Enum value 0 is always `UNSPECIFIED`.
- Use `oneof` for optional scalars (yields correct `Option<T>` in Rust via prost).
- Prefer field numbers 1-15 for high-frequency fields (1-byte tags on the wire).

## License

Apache-2.0, see [LICENSE](LICENSE).
