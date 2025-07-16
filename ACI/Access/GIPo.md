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

# GIPo

- Concept
	- Group IP Outer
	- Defined during fabric setup (default 225.0.0.0/15), cannot be changed
	- There is one GIPo range for the VRF and one for every BD under that VRF
	- BD GIPo is allocated once BD is created
	- VRF GIPo is allocated only when mcast is enabled in that VRF
	- Each GIPo is always a /28
	- Groups are advertised using ISIS (GM-LSP) #q
	- System GIPo is 239.255.255.240
- Verify
	- `show isis internal mcast routes gipo`

