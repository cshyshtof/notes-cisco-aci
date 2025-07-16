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

# AD

- If two protocols have the same AD, a tie-breaker is the default protocol's AD
- AD
	- Directly connected -0
	- Static to interface/NH - 1
	- EIGRP Summary - 5
	- eBGP - 20
	- EIGRP Internal - 90
	- IGRP - 100
	- OSPF - 110
	- ISIS - 115
	- RIP - 120
	- EIGRP external - 170
	- iBGP - 200
	- BGP backup - 220
	- Unknown (not valid) - 255

