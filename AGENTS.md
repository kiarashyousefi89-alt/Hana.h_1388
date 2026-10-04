# Base44 Dev Environment

## What this is
A single static HTML file (`hana_birthday.html`) — a birthday celebration page for "Hana". No backend, no build step, no dependencies, no external services.

## Running
`docker compose -f docker-compose.base44.yml up -d` serves the page via nginx on host port 3000.

- nginx runs as `user root` (the repo dir is mode 700, so the default `nginx` worker user cannot read the bind mount).
- `nginx.base44.conf` sets `hana_birthday.html` as the index; `nginx.base44.main.conf` is the full main config (needed to override the user directive).
- The source is bind-mounted read-only, so edits to `hana_birthday.html` are reflected on the next browser refresh — no rebuild needed.

## Verification
`curl -s http://localhost:3000/` should return the HTML starting with `<!doctype html>`.

## No secrets
The app requires no external credentials.
