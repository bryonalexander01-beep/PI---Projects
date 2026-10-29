# Lessons learned

Short version: most of the hard days were not about any one tool.
They were about two devices both thinking they were in charge, or
one device still pointing at a router that was no longer there.

- One DHCP server. If the router and the Pi both hand out addresses,
  devices will get inconsistent gateways and DNS, and the failures
  will look random.
- One DNS source for local names. If a device also queries a public
  or ISP resolver, that resolver can win the race and a local short
  name will fail, even though the local filter answers correctly.
- After a router swap, check the whole chain, not just the router.
  Router, wired link, switch, and Pi all have to be on the same
  network, and a device that looks online over Wi-Fi can still be
  unable to reach a service on the wired side.
- A device that shows no address at all has not joined the network
  yet. That is a Wi-Fi association or password problem first, and a
  DHCP problem second. A network-settings reset helps, but a full
  power unplug is what actually cleared a stuck TV here.
- For monitoring, check by address, not by a name that depends on
  the thing you are monitoring. Otherwise a DNS problem masquerades
  as every service being down.
- For a container monitor, host networking and firewall rules
  interact: fixing one can expose the other.
- Keep the ISP gateway around if it belongs to someone else, even
  when it is not in use. Unplugged and stored is fine; thrown away
  is not.
- When a router is replaced, do not assume the old network name and
  password carried over. Devices remember networks by name, and a
  new name means a new setup for each device, including its DNS
  settings.
- Do not set up a whole-house VPN just because the router supports
  it. Without a specific use — a device that cannot run VPN software
  itself, or a need to hide all house traffic — it mostly costs
  speed and breaks streaming, for no clear benefit.
