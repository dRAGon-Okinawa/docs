---
description: >-
  Description of the Silo. Optional. Used by the Language Query Router to choose
  the best Silo among Farm chain.
---

# Silo Description

When you make up a Farm with two or more Silos, you may need to only query the best Silo in order to reduce cost and response latency.

1. Setup a Farm with a specific Query Router : LANGUAGE MODEL
2. On each Silo put a description about the holded documents

User query will now go through LLM in order to decide where to route the given query to a specific Silo.
