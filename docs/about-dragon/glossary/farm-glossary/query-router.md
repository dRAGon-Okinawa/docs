---
description: Query Router to best choose Silos based on the user request.
---

# Query Router

## DEFAULT

Farm will use all Silos to perform queries on in order to reply to user request. Each Silos will be queried to find and join the best documents fragments.

## LANGUAGE MODEL

Instead of querying all Silos, the Farm will ask LLM to choose between one or more Silos. LLM will make its choice based on the [Silo Description](../silo-glossary/silo-description.md).

### Fallback Strategies

If LLM is unable to make a choice (no relevant Silo or network error) you can setup a fallback strategy.

#### FAIL (Default)

Farm will refused to reply user query, the RaaG pipeline will fail to reply.

{% hint style="info" %}
To use it, add this Retrieval Augmentor setting :\
\`languageQueryRouterFallbackStrategy\` = \`FAIL\`
{% endhint %}

#### DO\_NOT\_ROUTE

Farm will NOT use any Silo to reply. Only the LLM knowledge will.

#### ROUTE\_TO\_ALL

All Silos will be used to find relevant documents on. This strategy is similar to choosing 'DEFAULT' as the Query Router type. Useful to check over all Silos if user query doesn't contain words that the LLM could use to match on.
