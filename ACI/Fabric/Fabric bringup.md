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

# Fabric bringup

- CIMC
	- Default CIMC password cane be empty or `password` or `Insieme123`
	- NIC Mode must be *Dedicated*, and NIC Redundancy must be *None*
	- Otherwise, APIC-facing leaf will be discovered, but will remain as inactive
- ISO Install
	- Flashing new APIC takes over 3h to complete via vKVM, use vMedia
	- Increase HTTP session timeout to max value
	- KVM stops showing the output once installer starts
	- Enable SOL via CIMC CLI to watch the installation progress
	- When using SOL, physically disconnect the console port
	- `scope sol; set enabled yes; set baud-rate 115200; commit; connect host`
- Bootstrap
	- CLI
		- Up to 5.x
		- You can restart the initial config dialog by pressing Ctrl-C
	- GUI
		- Since 6.x
		- Use CLI to provide APIC OOB IP only and admin password
		- All bootstrap is done via GUI
		- You can add other APICs via CIMC or OOB (watch for FWs on the path)
		- To use OOB you must perform initial CLI config of each APIC (OOB IP)
- Verify
	- `acidiag verifyapic` - check cert validity

