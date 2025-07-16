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

# Domain

- Concept
	- Defines what will be connected to the fabric
	- Indirectly defines which **VLANs** are allowed to be assigned on interfaces
	- You can categorize it by type of access, but also by environment (test, prod)
- Types
	- **VMM** - created during VMM integration (*Virtual Networking*)
	- **Physical** - bare metal, routers, hypervisor without VMM integration
	- **L3Out** - external routing devices, no EPs
	- **L2Out** - not really used anymore
	- **FC** - becomes obsolete
- Config
	- *Fabric > Access Policies > Physical And External Domains*
	- *VLAN Pool*; - Only one pool can be assigned to a domain; - Do not assign the same VLAN pool to different domains (loops may occur)
	- *AAEP* - many domains can be assigned to one AAEP
- Validation
	- *System > System Settings > Fabric Wide Settings > Enforce Domain Validation*
	- If not enabled, F0467 is raised (Invalid Path) but traffic is allowed
	- It is recommended to enable, cannot be disabled #best
	- Take a new snapshot after enabling it, as a revert to previous one will fail

