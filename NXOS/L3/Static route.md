---
type: zettel
---

```meta-bind-button
label: Set next review
hidden: false
id: review
style: primary
actions:
  - type: command
    command: review-obsidian:future-review
  - type: input
    str: "next 7 days"
```

# Static route

- Static
	- `(G) ip route <net> <mask> <gw> <AD>`
	- Static to LAN can be used only if there is a device with `ip proxy arp` enabled
	- Static route to interface makes this network a connected
	- Only BGP and EIGRP are able to pick up such networks
	- `(G) ip route <net> <mask> [<interface>] dhcp`; Add a static route with NH acquired from DHCP

