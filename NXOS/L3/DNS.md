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

# DNS

- Config
	- `ip domain-name <name> [use-vrf <name>]`
	- `ip domain-list <name> [use-vrf <name>]`; - Additional domain names; - Can be multiple lines
	- `ip name-server <ip1 .. ip6> [use-vrf <name>]`
	- `ip domain-lookup`
	- `show hosts`

