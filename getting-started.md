---
description: Let's discover dRAGon in less than 5 minutes.
---

# Getting Started

## dRAGon Startup Guide <a href="#dragon-startup-guide" id="dragon-startup-guide"></a>

{% hint style="danger" %}
dRAGon lacks of authentication and authorization mechanisms. It is not recommended to expose it to the internet or unsafe networks. These mechanisms will be implemented in a near future.
{% endhint %}

{% hint style="warning" %}
dRAGon is still in active development stage and may contain bugs or incomplete features. No smooth upgrade path is guaranteed between versions. Can be broken at any time.
{% endhint %}

### 1. Launch <a href="#id-1-launch" id="id-1-launch"></a>

{% hint style="success" %}
The best way to run dRAGon is to use Docker. If you want to run it without Docker, you can use Gradle and follow [dRAGon Development Mode](contributing/dragon-development-mode.md).
{% endhint %}

{% code overflow="wrap" %}
```
docker run --rm -p 1985:1985 -v $(pwd)/data:/data -v $(pwd)/documents:/documents --name dRAGon ghcr.io/dragon-okinawa/dragon:latest
```
{% endcode %}

{% hint style="info" %}
`/data` and `/documents` are optional volumes to mount. You can mount any directory you want!

* `/data` is used to store the dRAGon database and settings. If you want to keep your data between reboots, you should mount this volume.
* `/documents` is used here to store the documents to be indexed inside the vector store (eg. by using FileSystem Ingestor).
{% endhint %}

### 2. Access <a href="#id-2-access" id="id-2-access"></a>

Open your browser and go to [http://localhost:1985](http://localhost:1985/).

### 3. Configure <a href="#id-3-configure" id="id-3-configure"></a>

{% hint style="warning" %}
This section lacks useful information. It is a work in progress and will be updated soon.
{% endhint %}
