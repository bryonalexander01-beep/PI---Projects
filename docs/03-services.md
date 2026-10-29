# Services

All of these run in containers or as small local services on the Pi,
unless noted otherwise. Access details, ports, and addresses are
intentionally omitted — use your own local addresses and links.

## Dashboard

A simple local web page that gathers status and quick links. It
refreshes on load and on a timer, and pulls live data from a small
local script. Think of it as a home page for the Pi, not a public site.

## DNS filtering / DHCP

A network-wide DNS filter and DHCP server. It blocks known ad and
tracker domains for devices on the home network, and hands out local
addresses. Upstream DNS is a public resolver. The admin interface is
local only.

House-wide rollout lesson: if the ISP gateway cannot change DNS, the
workaround is to shrink its DHCP pool and let the Pi handle DHCP for
everything else, so devices actually use the Pi for DNS. Devices pick
this up when their DHCP lease renews, or sooner if their Wi-Fi is
toggled.

## Containers / Portainer

Containers are managed with a web-based container manager. It is used
to start, stop, update, and inspect containers, and to run commands
inside them when needed. No container here gets access to the host
Docker socket unless there is a specific reason for it.

## Uptime monitoring

A self-hosted uptime monitor watches the local services and reports
whether each one is up. A useful detail: monitors should check the
service by its local address, not by a short local name that itself
depends on DNS, or a DNS hiccup will look like every service is down.

One setup gotcha worth remembering: containers on a default bridge
network do not always reach services on the host's local address the
way a laptop on Wi-Fi does. Running the monitor on the host network
fixed that here, where a firewall rule then became the next thing to
check for the monitor's own port.

## Short local links

A tiny redirect service maps short local names to local services, so
services can be reached by a short name instead of an address and a
port. The rule adopted here: every new local web service gets a short
link at setup time, no exceptions, so there is always one landing page
to remember.

Single-label names have quirks: browsers may treat a bare short name
as a search instead of an address, and a device whose DNS list
includes a non-local resolver can fail to resolve it at all. Typing
the full local address, and making sure the device's DNS is only the
local filter, fixes most of that.

## AI assistants (experiments)

Two self-hosted AI assistant containers were tried:

- A chat-style assistant with a web control UI, channels, and
  bring-your-own-model support
- A longer-running agent with persistent memory, tools, and a
  dashboard

Both need interactive setup the first time — model choice, and an
auth step for a non-local dashboard. That setup is not documented
here, because it involves credentials. Treat both as experiments,
not as finished services, until that first setup is done and the
dashboards actually load.

## Coding assistant container

A containerised coding assistant, built from a standard Node image
with common tools, no host Docker socket, and separate volumes for
its config and its workspace. Login is done interactively inside the
container the first time, and persists in its config volume. A shell
alias on the Pi makes it a one-word command to start.

This is not a build machine for large desktop projects — it is a
place to work on small projects from the Pi.
