# ente-museum-build

Weekly build of [Ente](https://github.com/ente-io/ente)'s server, museum, for a self-hosted instance that runs
without Docker on a shared host.

It builds the same commit that Ente publishes as `ghcr.io/ente/server:latest` and adds one patch. Two
environment variables choose where museum listens:

- `MUSEUM_LISTEN_HOST` is the API host. Upstream binds `:<port>`, which means all interfaces.
- `MUSEUM_METRICS_ADDR` is the Prometheus address. Upstream binds `:2112`.

Without these variables, the binary behaves exactly like upstream. On a shared host, high ports are open to the
internet, so the instance sets both variables to `127.0.0.1` addresses.

Each release, `museum-<commit>`, contains `museum-linux-amd64.tar.gz`. The archive holds the static binary,
`configurations/`, `migrations/`, `mail-templates/`, `web-templates/`, `GIT_COMMIT` and `krlo-patch.diff`. The
release also has a `.sha256` file.

Ente is licensed under AGPL-3.0. The patch is in each archive, and the source is the linked upstream commit.
