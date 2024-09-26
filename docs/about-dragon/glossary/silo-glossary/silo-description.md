---
description: >-
  Description of the Silo. Optional. Used by the Language Query Router to choose
  the best Silo among Farm chain.
---

# Silo Description

When you make up a Farm with two or more Silos, you may need to only query the best Silo in order to reduce cost and response latency.

To do so, setup a Farm with a spcific Query Router : LANGUAGE MODEL\
User query will go through LLM in order to decide where to route the given query.
