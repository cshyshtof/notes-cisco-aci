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

# VRF

- Concepts
	- All unicast and multicast routing protocols support VRFs
	- By default, NX-OS uses the VRF of the incoming interface to select RIB
	- You can configure a route policy to set the VRF for incoming packets
- Predefined
	- `management`
		- Management purposes only
		- Only the `mgmt0` can be in the management VRF
		- The `mgmt0` cannot be assigned to another VRF
		- `write erase boot` does not remove the management VRF configurations
	- `default`
		- The default VRF is similar to the global routing table in IOS
- Config
	- `(G) routing-context vrf <vrf>`; Change default VRF context
	- `(G) vrf context <name>`; Static routing, PIM RP
	- `(IF) vrf member <name>`; All L3 configs are removed
	- `(G) system vrf-member-change retain-l3-config`; Keep L3 configuration when changing VRF membership
- Leaking
	- NX-OS supports route leaking (import or export) between VRFs
	- By default, the maximum number of IP prefixes leaked on-way is 1000
	- There is no limit on the number of routes leaked between non-default VRFs
	- Routes in the BGP default VRF can be imported directly
	- Any other routes in the default VRF should be redistributed into BGP first
- Services
	- `(G) snmp-server host <ip> [filter-vrf <name>] [use-vrf <name>]`; - Filter-vrf filters information from the selected VRF to this server; - Use-vrf is used to find reachability for the server
	- `(G) ip domain-list <name> [all-vrfs] [use-vrf <name>]`

