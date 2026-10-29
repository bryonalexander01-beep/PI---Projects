# Roadmap / on hold

## Next, when there is a reason

- Finish the interactive setup for the two AI assistant experiments,
  or drop one of them. Running both at once was an experiment, not a
  plan, and the better one should win.
- Add notifications to the uptime monitor, so a down service is
  actually noticed, not just visible on a dashboard.
- Verify that the dashboard, DNS filter, and redirect service all
  survive a Pi reboot, rather than assuming they will.
- Re-check the short links on mobile after any router change, since
  mobile DNS settings are per-network and do not carry over to a new
  network name automatically.

## Deliberately on hold

- A bigger router / network upgrade. The current holdover router
  does the job, including a multi-gig WAN port for a future faster
  plan. A larger upgrade is a wait-for-a-sale item, not a buy-now item.
- A whole-house VPN on the router. No use case was identified, so
  it stays off. The VPN app on individual devices covers the cases
  that actually come up.
- TV ad-blocking beyond DNS filtering. DNS blocking cannot remove
  on-screen ad slots, and blocking lists for TVs are a per-device
  check-first job, not a blanket rule.
- Any service that would need inbound ports, public DNS, or a
  certificate installed on every device. Those were considered and
  set aside in favour of keeping everything local and simple.
