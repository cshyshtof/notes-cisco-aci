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

# APIC

- Attached
	- Leaf-attached
	- L3-attached
		- APICs connected to IPN are considered part of Pod 0
		- Only APICs can be in Pod 0
		- APIC fabric IPs are user configurable, not assigned from Pod TEP pool
		- Each APIC fabric IP can be in a different subnet
		- APIC cluster can be placed in behind FWs
	- Virtual
		- Supported on ESXi servers directly connected to fabric or via IPN L3
		- No mixed cluster support, either all virtual or all physical
		- Supports all types of deployments: Remote Leaf, Multi-Pod, Multi-Site
		- Port Group
			- VLAN 0 (required for APIC LLDP discovery)
			- ACI Infra VLAN
			- Other inband VLANs
		- From 6.1(1) you can migrate between physical and virtual (and vice versa)
- Interfaces
	- Each APIC must be dual-connected to a pair of leaf switches
	- It's an fault-tolerance (active-backup)
	- vPC is not used, so you can connect to any two leaf switches
	- On 4-port VIC, interfaces 1 and 2 as well as 3 and 4 form internal bonds
	- APIC must be connected to the fabric with ports 1 and 3
	- `bond0`
		- Inband bond towards leaf switches
		- `bond0.<infra VLAN>` - in-band management, IP from TEP pool
	- `bond1`
		- OOB bond towards management switches
		- `oobmgmt` - APIC management, IP assigned by admin during initial setup
	- Verify
		- `apic# cat /proc/net/bonding/bond0`
		- `apic# show lldp` - shows infra VLAN
		- `apic(bash)# show lldptool {in | out} eth2-1`
		- *System => Controllers => apic => Interfaces*

