# OpenClaw Agent (placeholder)

> **Not yet available.** This is a scaffold entry — `available` is `false` so it will not
> appear in the market until you provide a real image.

OpenClaw is a **CLI coding agent** (like Claude Code / OpenCode) that connects to your SkillHub
private registry. It has no native web UI, so on a web app platform it is packaged as a
container running the CLI behind a **ttyd web terminal** (browser-based shell).

## To enable
1. Build a wrapper image (see the Dockerfile sketch in `docker-compose.yml`): base + the
   OpenClaw CLI install + `ttyd` on port `7681`.
2. Push it to your Aliyun ACR.
3. Set `image:` in `docker-compose.yml`, flip `available` to `true` in `config.json`, bump
   `tipi_version`, commit, and Update App Stores.
