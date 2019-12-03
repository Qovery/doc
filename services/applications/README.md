---
description: Easily manage your applications
---

# Applications

Applications are easy to manage on Qovery. To make it short:

* **1 project can have multiple applications**
* **1 application can only belong to 1 project**

**An application repository should contain a Dockerfile**. It should be able to build the Application and generate an image containing it \(look at the [Dockerfile page](dockerfile.md) to know more about it\).

To finish, in order to deploy to Qovery, you need to add a Qovery configuration. Here is the minimal configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
```
{% endtab %}
{% endtabs %}

Commit this file to your repository, push it and it's automatically deployed.

## Add services

You can find other proposed services by Qovery like:

| Services | Comments |
| :--- | :--- |
| [Network](../network/) | Custom DNS, SSL/TLS, Routes etc... |
| [Databases](../databases/) | SQL or NoSQL databases |
| [Brokers](../brokers/) | Message queuing systems |
| [Storages](../storage/) | Share data against your applications |

It's as easy as just adding a few lines in your configuration file! Also add the [SDK](../../extending-qovery/sdks.md) to be able to have zero credentials management.

