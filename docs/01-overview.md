# Overview

A single-board computer at home runs a handful of small services. It is
wired to the home network, not exposed to the internet, and it is meant
to be boring: up, quiet, and easy to restart.

In broad strokes, it does:

- A local dashboard that pulls together status and links in one place
- Network-wide DNS filtering, so ads and trackers are blocked for devices
  on the home network without installing anything on each device
- Container hosting, so services can be added, updated, and removed
  without disturbing each other
- Uptime monitoring, so it is obvious when a local service is down
- Short local links, so services can be reached by a short name instead
  of remembering addresses and ports
- A couple of self-hosted AI assistant experiments, and a containerised
  coding assistant for working on projects from the Pi

That is the whole pitch. Everything else in this repo is just notes on
how those pieces fit together, and what went wrong along the way.
