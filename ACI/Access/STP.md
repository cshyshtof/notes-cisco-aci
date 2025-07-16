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

# STP

- Concept
	- ACI does not participate in STP, but it transports unaltered BPDUs
	- BPDUs are carried using EPG FD_VLAN VXLAN VNID, not BD VXLAN VNID
- Design
	- Use double-sided vPC to legacy infrastructure to limit numer of STP nodes
	- If possible, limit VLANs per DC, so only single fabric extension exists
- RSTP
	- An external switch expects only one switch on the other side of the link
	- It sends a proposal and another switch behind ACI responds
	- Ports change state to forwarding/blocking
	- A third switch may send another proposal
	- The port with already agreed state ignores it, loop can occur
	- `(IF) spanning-tree port-type normal`; Disables Bridge Assurance
	- `(IF) spanning-tree link-type shared`; - Shared port does not use proposal-agreement; - Classical STP timers are used; - Convergence is slower, but loops can be avoided
- MST
	- MST sends BPDU using native VLAN
	- If native VLAN is configured on a leaf, it will transport those BPDUs
	- Otherwise, dedicated EPG must be added with a static path as 802.1p
	- *Fabric > Access Policies > Policies > Switch > Spanning Tree*
	- *Region Policies* - MST mappings
	- *Enable Bpdu Filter for Extended Chassis Ports* #q
- TCN
	- ACI reacts to TCN, flushing all EPs in VLAN where TCN was received
	- TCN can cause massive glean process when EPs are flushed
	- To avoid flushing, define different encap for EPs directly connected to ACI
	- Domain1 can contain an AAEP for interfaces in Pod 1
	- Domain2 can contain an AAEP for interfaces in Pod 2
	- Each domain has own VLAN pool, but with an overlapping VLAN range
	- Different FD_VLAN is assigned to the same VLAN in each pod
	- This minimizes the impact of TCN, as only EPs in single DC are flushed #q
- Filtering
	- *Fabric > Access Policies > Policies > Interface > Spanning Tree Interface*
	- BPDU Guard, BPDU Filter

