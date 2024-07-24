# LibreChat

## As an AI Endpoint (OpenAI compatible) <a href="#as-an-ai-endpoint-openai-compatible" id="as-an-ai-endpoint-openai-compatible"></a>

```yaml
endpoints:
  custom:
    - name: "dRAGon"
      apiKey: "YOUR_API_KEY"
      baseURL: "http://localhost:1985/api/raag/v1"
      models:
        default: ["your-raag-model-name"]
        fetch: true
      titleConvo: true
      titleModel: "your-raag-model-name"
      titleMethod: "completion"
      modelDisplayLabel: "dRAGon"
      iconURL: "https://raw.githubusercontent.com/dragon-okinawa/dragon/main/static/img/dragon_okinawa_icon.png"
      userIdQuery: true
      summarize: false
```

## As a LangChain.js Plugin <a href="#as-a-langchainjs-plugin" id="as-a-langchainjs-plugin"></a>

{% hint style="warning" %}
**WORK IN PROGRESS**

This section lacks useful information. It is a work in progress and will be updated soon.
{% endhint %}

## As an OpenAPI Plugin <a href="#as-an-openapi-plugin" id="as-an-openapi-plugin"></a>

{% hint style="warning" %}
**WORK IN PROGRESS**

This section lacks useful information. It is a work in progress and will be updated soon.
{% endhint %}
