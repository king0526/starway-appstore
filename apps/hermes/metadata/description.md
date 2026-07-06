# Hermes Agent (placeholder)

> **Not yet available.** Scaffold entry — `available` is `false` until a real image is provided.

Hermes is an AI agent tool slated for the Starway store. Deployment details (Docker image,
whether it has a web UI or is a CLI, ports, env) are pending.

## To enable
- **If it has a web UI:** set `image:` and the real `internal_port` in `docker-compose.yml`.
- **If it is a CLI:** wrap it with a `ttyd` web terminal like the OpenClaw app.
- Then flip `available` to `true`, bump `tipi_version`, commit, and Update App Stores.
