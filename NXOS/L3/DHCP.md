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

# DHCP

- Concepts
	- NX-OS supports DHCP client on SVIs, Ethernet, and management interfaces
	- `(IF) ip address dhcp`; Automatically configures 0/0 and DNS
	- DHCP relay and DHCP client are not supported on the same switch
	- DHCP snooping is not enforced on the SVI with DHCP client

