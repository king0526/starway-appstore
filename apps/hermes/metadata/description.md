# Hermes Agent

Hermes is Nous Research's personal **AI agent**. This app runs its **web dashboard** — chat,
skills, sessions, MCP servers, and usage insights.

- Image: `nousresearch/hermes-agent:latest`
- Internal port: `9119`
- Protected by **basic auth**: set an admin username/password at install
  (`HERMES_DASHBOARD_BASIC_AUTH_USERNAME` / `_PASSWORD`). Hermes refuses a public bind without it.

## Notes
- After install, open the dashboard, log in, and configure your model provider / API keys.
- Data is not mounted to a host volume in this build (the image ships a pre-populated
  `/opt/data` owned by the `hermes` user; a plain empty bind-mount would break it). For
  persistence, run with `HERMES_UID`/`HERMES_GID` matching the host and mount `/opt/data`.
- China/starway: `nousresearch/hermes-agent` is large — mirror it to your Aliyun ACR if the
  pull is slow.
