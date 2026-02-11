---
id: AODV
aliases:
  - AODV
tags:
  - University
  - UbiComp
---

# Ad Hoc On-Demand Distance Vector (AODV)

- DSR include source routes in packet headers
    - *Making it varies in size causing degraded performance*

- Try to improve DSR by maintaining routing table in each node
- RREQ are fowarded in similiar manner as DSR
- Send Route Reply (RREP) as answer

- Use *destination sequence numbers* to basically version route.
- And intermediate node may send RREP if its know more recent path
    - *Don't say anything if its older*

## Route Error

- If node X can't foward parcket (S -> D) on link (X, Y) it generate RERR message that the link is broken
- 

**Midterm focus on DSR + AODV**

# DSDV (Not in exam)
# ZRP (Not in exam)
- Intrazone Routing 

