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

# RIB

- RIB/FIB
	- `(VRF-AF) maximum routes <#> [<threshold %> [reinstall <threshold %>] | warning-only]`; Routes that previously exceeded the maximum limit can be reinstalled
	- `show forwarding inconsistency`
	- `show consistency-checker forwarding unicast`
	- `clear forwarding ipv4 route`
	- `show forwarding ipv4 adjacency`
	- `show forwarding ipv4 route`
	- `show routing memory estimate routes <#> next-hops <#>`
	- `show system internal access-list dest-miss stats`; Displays statistics for packets dropped due to missing the FIB routes for the destinations (DEST MISS)
- Load-sharing
	- `(G) ip load-sharing ...`
	- `show ip load-sharing`
	- `show routing hash <src-ip> <dst-ip> [<src-port> <dst-port>] [vrf <name>]`
- Redistribution
	- Get routes which are in a RIB and belong to redistributed protocol
	- `show ip route <protocol>`
	- Get connected routes, covered by redistributed protocol with a `network`
	- `show ip route connected <addr>`
	- Route to be redistributed must be in the RIB
	- Chain distribution on one router is NOT possible, ex.: EIGRP > RIP > OSPF
	- EIGRP routes will be redistributed into RIP
	- EIGRP routes will NOT be in OSPF
	- Separate redistribution from EIGRP to OSPF is required

