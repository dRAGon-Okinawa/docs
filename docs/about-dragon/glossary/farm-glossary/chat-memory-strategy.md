---
description: Evicts old messages or tokens based on the strategy.
---

# Chat Memory Strategy

* MAX MESSAGES : Evicts old messages when reaching limit
* MAX TOKENS : Evicts old **messages** when reaching limit

{% hint style="info" %}
To define MAX MESSAGES value (default to 10), add this Retrieval Augmentor setting key :\
`historyMaxMessages`
{% endhint %}

{% hint style="info" %}
To define MAX TOKENS value (default to 3000), add this Retrieval Augmentor setting key :\
`historyMaxTokens`
{% endhint %}
