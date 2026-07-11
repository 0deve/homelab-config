# Homelab config

Docker Compose configuration for my self-hosted home lab, managed with [Dockge](https://github.com/louislam/dockge). Each service lives in its own stack under `stacks/`, exposed through Cloudflare Tunnel and reachable remotely via Tailscale.

## Structure

- `dockge/` — Dockge itself, the compose manager. Stacks live in `/opt/stacks` on the host.
- `stacks/<name>/` — one directory per stack, each with its own `compose.yaml`. Stacks that need secrets have a `.env.example` — copy it to `.env` and fill in real values.

## Services

**Media**
- `jellyfin` — media server (NVIDIA hardware transcoding)
- `arr-stack` — qBittorrent, Radarr, Sonarr, Prowlarr, Bazarr, Jellyseerr, Recyclarr, FlareSolverr (Tdarr config kept but commented out)
- `immich` — photo backup (with Postgres + Redis)

**Network / access**
- `cloudflare` — Cloudflare Tunnel for public access
- `tailscale` — remote access to the LAN
- `nginx-proxy-manager` — reverse proxy
- `adguard` — DNS-level ad blocking
- `speedtest-tracker` — periodic connection speed tests

**Monitoring / management**
- `uptime-kuma` — uptime monitoring
- `homepage` — dashboard
- `diun` — Docker image update notifications to Discord

**Apps**
- `stirling-pdf` — PDF toolbox
- `filecodec` — tool site + its own Cloudflare tunnel
- `website` — personal website (nginx)
- `discord-bot` — custom server-health / Jellyseerr-approval Discord bot

[Website Source Code](https://github.com/0deve/website)

[File Share Source Code](https://github.com/0deve/file-sharing)

[TTS Source Code](https://github.com/0deve/TTS-app)

