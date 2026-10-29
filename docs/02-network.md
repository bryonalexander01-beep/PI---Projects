# Network, in general terms

The home internet comes in over fiber. A separate optical terminal
converts fiber to Ethernet. That Ethernet goes to a Wi-Fi 7 router with
a multi-gig WAN port, which is the main router for the house.

From there, the layout is roughly:

- Router -> a wired link through the house wiring -> a switch -> the Pi
- Other devices connect over Wi-Fi to the router, or wired to the switch
- The ISP-provided gateway is not in use; it is unplugged and kept
  aside, as it belongs to the living arrangement, not to this setup

A few design choices, stated generally:

- One DHCP server only. The router's built-in DHCP is off, and the Pi
  handles DHCP for the home network. Two DHCP servers on one network
  cause exactly the kind of random, hard-to-diagnose failures you would
  expect.
- One DNS filter. Devices get the Pi as their DNS server, so filtering
  applies network-wide.
- The Pi has a fixed local address, and the router is the gateway for
  the home network. Those specific addresses are not listed here on
  purpose — they are local to one house.
- Remote access, when needed, is through a private mesh tunnel, not
  through port forwarding. No inbound ports are opened for these
  services.

## Router swap notes

Swapping the main router is a good moment to check, in order:

1. Does the new router get a public address from the fiber terminal?
   A power cycle of the terminal is often needed so it releases the
   old router's lease.
2. Is the router's local address the same as the old gateway address
   the rest of the network expects? If not, update it before chasing
   other problems.
3. Is there exactly one DHCP server, and is it reachable from both
   wired and Wi-Fi devices?
4. Are wired devices actually on the same network as Wi-Fi devices?
   A switch, a wired-through-the-house link, or a similar hop can
   silently leave part of the network on an island if its uplink
   still points at the old router.
5. Do TVs and other stubborn devices get a fresh start? A full power
   unplug, not just a standby reboot, clears network state that a
   settings reset alone sometimes does not.
