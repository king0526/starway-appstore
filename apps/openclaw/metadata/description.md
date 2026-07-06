# OpenClaw Gateway

OpenClaw is a CLI coding-agent platform. This app runs its **gateway** — an HTTP/WebSocket
endpoint (7 plugins: browser, canvas, device-pair, file-transfer, memory-core, phone-control,
talk-voice) that channels and clients connect to.

- Image: `openclaw/openclaw:latest`
- Internal port: `18789`
- A **gateway token** is generated at install; connecting clients must present it
  (`OPENCLAW_GATEWAY_TOKEN`). The gateway refuses to bind on a non-loopback address without it.

## Notes
- The gateway is an API/WebSocket endpoint, **not a full browser dashboard** — "Open" shows the
  gateway HTTP surface. Point your OpenClaw CLI / channels at it.
- This build starts with `--allow-unconfigured` and does not persist config across reinstall.
  For a persistent, fully-configured gateway (registry/auth/skills), run `openclaw setup` and
  mount a data volume.
