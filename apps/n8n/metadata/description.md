# n8n

n8n is an extendable **workflow automation** tool. Connect anything to everything with 400+ integrations, a visual node editor, and native AI/LLM nodes.

- Image: `docker.n8n.io/n8nio/n8n`
- Internal port: `5678`
- Data is persisted under the app data directory (`/home/node/.n8n`), so workflows and credentials survive restarts.

## Notes for China / starway deployments

- The default registry (`docker.n8n.io`) may be slow or blocked behind the GFW. If the pull hangs, mirror the image to your Aliyun ACR and change the `image:` line in `docker-compose.yml`.
- Timezone defaults to `Asia/Shanghai`; adjust `GENERIC_TIMEZONE` / `TZ` as needed.
