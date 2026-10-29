# Pi Projects

A small home Raspberry Pi setup, documented in general terms.

This is a home lab, not a production system. The goal is simple: one small
computer that quietly handles a few useful home jobs — a dashboard, local
DNS / ad blocking, containers, and uptime checks — without needing a big
server or a lot of upkeep.

Nothing in this repo is meant to be a copy-paste setup guide for someone
else's network. Addresses, hostnames, passwords, tokens, and other
site-specific details are intentionally left out. Treat anything that
looks like a placeholder (for example, `<pi-address>`) as something you
fill in for your own network.

## What lives here

- `docs/01-overview.md` — what the Pi does, in plain terms
- `docs/02-network.md` — how the home network is laid out, in general
- `docs/03-services.md` — the services running on the Pi, and what each is for
- `docs/04-lessons.md` — things learned the hard way, so they don't get repeated
- `docs/05-roadmap.md` — what's next, and what's deliberately on hold

## Ground rules

- No credentials, keys, tokens, or personal details in this repo.
- No internal addresses, hostnames, or network ranges.
- If a detail would only make sense for one specific house, it doesn't belong here.
- The Pi is a home tool, not a public server. Services here are for local use.
