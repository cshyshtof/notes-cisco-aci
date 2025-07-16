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

# VLAN

- Notes
	- Commands are executed after you exit from a VLAN submode
	- Disabling STP on native VLAN, but not on every other VLAN, can cause loops
- Reserved
	- `(G) system vlan <id> reserve`
	- Defaults are 3968-4095, and 4093-4095 are always reserved
	- `show system vlan reserved`
	- `show vlan internal usage`
- Shutdown
	- `(VLAN) state {active | suspend}`
	- `(VLAN) shutdown`
	- VLANs 1006-3967 cannot be suspended or shutdown
- Config
	- `(G) vlan configuration <id>`; - You can configure a VLAN before you create it; - Used mainly for IGMP snooping, QoS, VTP, etc.
	- `(G) system vlan long-name`; Enables 128 characters VLAN names
	- `(G) vlan <#>`; `  name <name>` must be unique
	- `show vlan id <#>`
- Native
	- `(IF) vlan dot1q tag native`
	- Enable native VLAN tagging, similar to legacy ISL
	- Not really used, avoid
- Autostate
	- `(G) system default interface-vlan autostate`; Enabled by default
	- `(IF) switchport autostate exclude {vlan <id> | all | except}`
	- `(SVI) autostate`; Enabled by default

