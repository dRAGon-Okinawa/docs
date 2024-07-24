# dRAGon Development Mode



{% hint style="warning" %}
**VISUAL STUDIO CODE DEV CONTAINERS**

In order to be as close as possible to the development environment, we **strongly** recommend using Visual Studio Code Dev Containers. You can find the configuration file in the `.devcontainer` folder.

If it's not possible please make sure you have the following tools installed with the **correct** versions:

* Java 17
* Gradle 8.7
* Node.js 20
* NPM 10
* "Unix like" System (Linux, MacOS)

However we do **NOT** accept any issues related to troubles encountered by **NOT** using the Dev Containers.
{% endhint %}

## Clone Repository <a href="#clone-repository" id="clone-repository"></a>

```
git clone https://github.com/dRAGon-Okinawa/dRAGon
```

## Prepare Dependencies <a href="#prepare-dependencies" id="prepare-dependencies"></a>

```
gradle npmInstall build
```

## Launching dRAGon <a href="#launching-dragon" id="launching-dragon"></a>

```
gradle bootRun
```

