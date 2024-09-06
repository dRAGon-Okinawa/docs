---
description: >-
  Identifier of the RaaG (RAG as a GPT). Must be unique. Used as the model name
  for your API calls.
---

# RaaG Identifier

Identifier of your Farm RaaG that will be used for your API calls like this one :

```python
from langchain_openai import OpenAI

llm = OpenAI(
    model_name="raag-identifier-will-be-here",
    openai_api_base="http://your.dragon.host:1985/api/raag/v1",
)

prompt = "What's dRAGon?"
llm.invoke(prompt)
```

{% hint style="info" %}
Must be alphanumeric (lowercased), hyphens allowed, validated by this REGEX : \
^\[a-z0-9\\-]+$
{% endhint %}
