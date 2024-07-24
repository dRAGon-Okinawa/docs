---
description: >-
  This command is used to dump the database to a JSON file. It can be used to
  backup the database or to move the database to another instance.
---

# Database Export

## Online Export <a href="#online-export" id="online-export"></a>

To export the database while the backend server is running, use the following API endpoint:

{% code overflow="wrap" %}
```bash
curl -X 'POST' 'http://localhost:1985/api/backend/command/database/export'
```
{% endcode %}

## Offline Export

{% hint style="info" %}
This command should only be used when the backend server is offline. Running this command while the backend server is running may not work as the database could be locked. To export the database while the backend server is running, use the API endpoint provided above.
{% endhint %}

## Using Gradle <a href="#using-gradle" id="using-gradle"></a>

{% code overflow="wrap" %}
```bash
gradle bootRun --args="--command=database-export --output=/path/to/dump.json"
```
{% endcode %}

## Using Java <a href="#using-java" id="using-java"></a>

{% code overflow="wrap" %}
```bash
java -jar backend.jar --command=database-export --output=/path/to/dump.json
```
{% endcode %}
