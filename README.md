# Starway App Store

A custom application store for the **Starway / aPaaS** platform, created from the official
Runtipi app-store template (schema v2). Use it to publish and maintain your own collection
of apps (n8n, dify, coze, …) independent of the official store.

## Repository Structure

- **apps/**: individual app directories. Each app folder (e.g. `whoami/`, `n8n/`) contains:
  - `config.json`: app metadata (see the config reference)
  - `docker-compose.yml`: services + `x-runtipi` metadata (schema v2)
  - `metadata/`:
    - `description.md`: markdown shown on the app detail page
    - `logo.jpg`: square (1:1) app icon
- **\_\_tests\_\_/apps.test.ts**: validation test suite (inherited from the template)
- **scripts/update-config.ts**, **config.js**, **renovate.json**: template tooling kept intact

> The app folder name **must equal** the `id` in that app's `config.json`.

## Included apps

| App    | Purpose                                  | Image                          |
| ------ | ---------------------------------------- | ------------------------------ |
| whoami | Smoke test — install first to verify     | `traefik/whoami`               |
| n8n    | Workflow automation (400+ integrations)  | `docker.n8n.io/n8nio/n8n`      |

## Add this store to the platform

1. Push this repo to a Git host the platform container can `git clone` **anonymously**.
   Behind the GFW, prefer **Gitee** or a **self-hosted** Git so the clone succeeds.
2. In the platform: **设置 → 应用商店 → 添加应用商店**
   - **名称 (name):** `Starway` (1–16 chars)
   - **地址 (url):** repo URL, e.g. `https://gitee.com/<you>/starway-appstore`
     (non-default branch: `https://.../starway-appstore/tree/<branch>`)
3. Open **应用市场**; install **Whoami** first to confirm the pipeline works end to end.
4. (Optional) Disable the official store so only Starway apps remain.
5. After pushing changes, click **更新应用商店 / Update App Stores** to pull.

## Add a new app

1. Copy an existing `apps/<app>` folder, rename it to the new app `id`.
2. Edit `config.json` (`id`/`name`/`short_desc`/`source`/`categories`/`port`).
3. Edit `docker-compose.yml` (image + `internal_port`, mark the entrypoint `is_main: true`).
   Do **not** write `ports:` — the platform handles reverse-proxy + host port mapping.
4. Replace `metadata/logo.jpg` (square) and write `metadata/description.md`.
5. Commit & push, then Update App Stores in the platform.

**Valid `categories`:** `network, media, development, automation, social, utilities,
photography, security, featured, books, data, music, finance, gaming, ai`.

> China/starway tip: point `image:` at an Aliyun ACR mirror when the upstream registry
> (docker.io / docker.n8n.io) is slow or blocked.

## Credit

Bootstrapped from the official template: <https://github.com/runtipi/example-appstore>
(see the guide at <https://runtipi.io/docs/guides/create-your-own-app-store>).
