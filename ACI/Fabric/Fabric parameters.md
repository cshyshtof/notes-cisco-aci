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

# Fabric parameters

- Fabric name is really used anywhere, but cannot be changed
- Fabric ID should be always 1
- TEP
	- Minimum /19 is recommended
	- First 32 IPs are dedicated for APICs
- Infra VLAN
	- Safe VLAN is 3967 or any value below 3914
- GIPo
	- Recommended default 225.0.0.0/15
	- Requires exactly /15

