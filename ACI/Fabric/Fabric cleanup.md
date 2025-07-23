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

# Fabric cleanup

- APIC
	- Cleanup APIC first, so reloaded switches will not fetch existing config
	- `acidiag touch clean`
	- `acidiag touch setup`
	- `acidiag reboot`
- Switches
	- `setup-clean-config.sh`
	- `loader> cmdline clear_config`


