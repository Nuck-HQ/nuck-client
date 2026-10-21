# nuck-client

The first-party **Nuck client** — a Tauri (Rust core) + React desktop app (ADR 0027).

> **Status: stub.** The client has not been started yet; this repository is reserved
> and holds no code. It exists so the three Nuck repositories are in place and
> discoverable.

## Where it sits

Nuck is split across three repositories:

| Repository | Role |
|---|---|
| [nuck-hq/nuck-protocol](https://github.com/nuck-hq/nuck-protocol) | The shared client/server contract crate (events, `/_nuck/v1` DTOs, permissions) |
| [nuck-hq/nuck-server](https://github.com/nuck-hq/nuck-server) | The backend, plus the design docs (ADRs, glossary, protocol spec) |
| **nuck-hq/nuck-client** (this repo) | The first-party client |

The client depends on `nuck-protocol`, so the wire format is compile-time verified
against the server.

## Planned shape (ADR 0027)

- **Tauri** desktop shell with a **React** UI.
- Rust core uses **`matrix-rust-sdk`** for Matrix sync and E2EE (ADR 0008).
- Depends on the protocol crate:

  ```toml
  nuck-protocol = { git = "https://github.com/nuck-hq/nuck-protocol.git", tag = "v0.2.0" }
  ```

The design record — ADRs, glossary, and the concrete `space.nuck.*` event registry
and `/_nuck/v1` endpoint inventory — lives in
[nuck-server/docs](https://github.com/nuck-hq/nuck-server/tree/main/docs).
