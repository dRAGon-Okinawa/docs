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
To use it, add this Retrieval Augmentor Setting to your farm :\
`languageQueryRouterFallbackStrateg`=`FAIL`
{% endhint %}

#### DO\_NOT\_ROUTE

Farm will NOT use any Silo to reply. Only the LLM knowledge will.

{% hint style="info" %}
Related Retrieval Augmentor Setting :\
`languageQueryRouterFallbackStrateg`=`DO_NOT_ROUTE`
{% endhint %}

#### ROUTE\_TO\_ALL

All Silos will be used to find relevant documents on. This strategy is similar to choosing 'DEFAULT' as the Query Router type. Useful to check over all Silos if user query doesn't contain words that the LLM could use to match on.

{% hint style="info" %}
Related Retrieval Augmentor Setting :\
`languageQueryRouterFallbackStrateg`=`ROUTE_TO_ALL`
{% endhint %}

### Language Query Router Prompt Template

[Default prompt template](https://github.com/langchain4j/langchain4j/blob/11855157dd71eb52d603c981a4e3ac561a336107/langchain4j-core/src/main/java/dev/langchain4j/rag/query/router/LanguageModelQueryRouter.java#L47) for the Language Query Router could be overridden by using this Retrieval Augmentor Setting inside your Farm :

{% hint style="info" %}
`languageQueryRouterPromptTemplate` = `Your Prompt Goes Here`
{% endhint %}
