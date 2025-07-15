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

# AAEP

- Concept
	- Attachable Access Entity Profile
	- Devices connected to the fabric may run different types of workloads (UCS-B)
	- Different workloads means different domains (L3Out, VMM)
	- Different domains are configured in different way (GUI location, parameters)
	- AAEP groups **domains** (VLANs) on a physical interface
	- Effective config: `switchport trunk allowed vlan ...`
- Config
	- *Fabric > Access Policies > Policies > Global > Attachable Access Entity Profile*
	- *Domains* - multiple domains of different types can be assigned
	- *Enable Infrastructure VLAN*; - Used when fabric needs to be extended, mainly for AVE or K8S; - Infra VLAN is added to the list of allowed VLANs
	- *EPG Deployment*; - Allowed VLANs are programmed on ports to which AAEP is assigned; - Another way is to add a static path in EPG
	- Assigned to *Interface Policy Group*
- VMM
	- VMM domain automatically derives physical interface policies
	- An override policy is useful where a VMM is connected via L2 node
	- You can enable LACP between a leaf and a L2 node
	- You can disable LACP between the VMM and L2 node (AAEP override)

