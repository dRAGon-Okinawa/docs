---
description: In dRAGon land, a Farm is a collection of Silos.
---

# What's a Farm?

```mermaid
flowchart LR
    Request-->Router
    subgraph farm1 [Farm]
        Router-->Silo1
        Router-->Silo2
        Router-->SiloN
        click Silo1 href "/about-dragon/glossary/whats-a-silo" "What's a Silo?"
        click Silo2 href "/about-dragon/glossary/whats-a-silo" "What's a Silo?"
        click SiloN href "/about-dragon/glossary/whats-a-silo" "What's a Silo?"
    end
    Silo1-->Response
    Silo2-->Response
    SiloN-->Response
```

{% hint style="info" %}
* You can aggregate multiple kind of Silos in a Farm, for example, you can have a Silo for your documents about your products, another Silo for your blog posts (extracted from URLs of a WordPress blog), and another Silo for Frequently Asked Questions (FAQs).
* There is no limit to the number of Silos you can have in a Farm, but you should keep in mind that the more Silos you have, the more time it will take to process the requests.
{% endhint %}
