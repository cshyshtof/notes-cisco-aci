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

# Physical

- Stomped CRC
	- With cut-through, a switch detects CRC after a frame has already been sent
	- The CRC field is stomped (special value is encoded), the output error increases
	- The packet is dropped at the next store-and-forward switch
	- If all switches are cut-through, the bad frame is delivered to the destination
	- Windows
		- `netstat -e`
	- Linux
		- `ip -s link show eth0`
	- `show interface counters errors non-zero`
- FEC
	- `show hardware internal tah mac hwlib show mac_errors fp-port`; Display the FEC Correctable and FEC UnCorrectable counters
- Link flap
	- Usually arise from faulty physical layer or protocol synchronization issues
	- Ethernet Port Manager (Ethpm) process manages Ethernet interfaces
	- `show system internal ethpm event-history interface <#>`
	- PIE
		- Platform Insights Engine (PIE) is supported on all Cloudscale ToR and EoR
		- PIE is an on-switch real-time root cause analysis application
		- `show pie interface ethernet <#> {link-flap-rca | transceiver-insights | link-down-rca}`
	- `attach module <#>`
		- `show system internal port-client link-event`
		- `show hardware internal tah link-events fp-port <#>`

