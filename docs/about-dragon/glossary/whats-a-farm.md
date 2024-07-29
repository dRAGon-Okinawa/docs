---
description: In dRAGon land, a Farm is a collection of Silos.
---

# What's a Farm?

```mermaid
flowchart LR
    Request-->Router
    subgraph farm1 [Farm]
        Router-->Silo1
        Router-->SiloN
        Router-->Granary1
        Router-->GranaryN
        Aggregator
        click Silo1 href "/about-dragon/glossary/whats-a-silo" "What's a Silo?"
        click SiloN href "/about-dragon/glossary/whats-a-silo" "What's a Silo?"
        click Granary1 href "/about-dragon/glossary/whats-a-granary" "What's a Granary?"
        click GranaryN href "/about-dragon/glossary/whats-a-granary" "What's a Granary?"
    end
    Silo1-->Aggregator
    SiloN-->Aggregator
    Granary1-->Aggregator
    GranaryN-->Aggregator
    Aggregator-->Response
```

{% hint style="info" %}
* You can aggregate multiple kind of Silos in a Farm, for example, you can have a Silo for your documents about your products, another Silo for your blog posts (extracted from URLs of a WordPress blog), and another Silo for Frequently Asked Questions (FAQs).
* There is no limit to the number of Silos you can have in a Farm, but you should keep in mind that the more Silos you have, the more time it will take to process the requests.
{% endhint %}
