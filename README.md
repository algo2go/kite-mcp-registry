# kite-mcp-registry

[![Go Reference](https://pkg.go.dev/badge/github.com/algo2go/kite-mcp-registry.svg)](https://pkg.go.dev/github.com/algo2go/kite-mcp-registry)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Pre-registered Kite app credentials store (admin-managed) for the
algo2go ecosystem. Backed by `algo2go/kite-mcp-alerts` shared SQLite
DB. Lets admins onboard Kite developer apps centrally so end-users
don't need to bring their own credentials.

Used by [`Sundeepg98/kite-mcp-server`](https://github.com/Sundeepg98/kite-mcp-server)
for admin-managed credential pool + per-user assignment via the
admin dashboard.

## Why a separate module?

Pre-registered credential storage is an admin-side primitive any
algo2go consumer that runs a hosted MCP server may need. Hosting as
a module:

- Centralizes the credential schema + lookup contract
- Pairs with `algo2go/kite-mcp-alerts` (shared DB)

## Stability promise

**v0.x — unstable.** Pin `v0.1.0` deliberately.

## Install

```bash
go get github.com/algo2go/kite-mcp-registry@v0.1.0
```

## Public API

- `Store` — credential CRUD with `*alerts.DB` backend
- `Credential` — DTO struct (Email, APIKey, APISecret, etc.)
- `NewStore(db *alerts.DB) *Store`

## Dependencies

- `github.com/algo2go/kite-mcp-alerts` v0.1.0 — shared DB backend

All algo2go deps published; no upstream `replace` directives needed.

## Reference consumer

[`Sundeepg98/kite-mcp-server`](https://github.com/Sundeepg98/kite-mcp-server)
— consumed across kc/credential_service.go, kc/store_registry.go,
kc/manager_*, kc/ops/admin_edge_registry_test.go, kc/ops/handler.go.

## License

MIT — see [LICENSE](LICENSE).

## Authors

Original design: [Sundeepg98](https://github.com/Sundeepg98) (Zerodha
Tech). Multi-module promotion (2026-05-10): algo2go contributors.
