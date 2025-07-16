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

# ARP

- ARP
	- On 9300, unicast ARP request to SVI is flooded to ports within the VLAN
	- `(IF) ip arp <ip> <mac>`; Static ARP is configured per interface
	- `(IF/G) ip arp timeout <sec>`; Default is 1500 sec.
- RARP
	- `(G) ip arp rarp fabric-forwarding [rate-limit <#>]`; Default rate is 200 fps
	- Requests an IP instead of a MAC
	- Provides only IP, not a mask or default gateway
	- DHCP is more cost effective and requires less maintenance than RARP
- Proxy ARP
	- `(IF) ip proxy-arp`; Not supported in a VXLAN DAG
- Local Proxy ARP
	- ARP responds to all ARP requests for IPs within the subnet
	- Useful on PVLAN subnets
	- Not supported on an interface with HSRP groups in multiple subnets
	- `(IF) ip local-proxy-arp`
	- `(SVI) ip local-proxy-arp no-hw-flooding`; - Suppresses ARP broadcasts on a VLAN; - Requires TCAM carving
	- `(G) hardware access-list tcam region arp-ether 256 double-wide`
- GARP
	- A request with own IP as source and destination to detect duplicates
	- `(IF) ip arp gratuitous {request | update}`; Enabled by default
	- `(IF) no ip arp gratuitous hsrp duplicate`
- Glean
	- `(G) hardware ip glean throttle`; Filters unnecessary CPU gleans for unreachable ARP NH
	- `(G) hardware ip glean throttle maximum <#>`; Default is 1000
	- `(G) hardware ip glean throttle syslog <#>`; Default is 1000
	- `(G) hardware ip glean throttle timeout <sec>`; - Timeout for installed drop adjacencies in FIB; - Default is 300 sec., use 30 sec intervals
- Verify
	- `show ip adjacency [summary]`
	- `show ip arp [summary]`
	- `show ip arp internal info interface <if>`

