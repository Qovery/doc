---
description: Add routes to your application
---

# Routes

Qovery allows you to manage routing to your multiple applications.

Here is how to do it in the Qovery configuration file:

1. Create a router and name it
2. You can optionally request a dns name
3. Create associated routes paths to an application

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
...
routers:
  - name: backend-router
    dns: api.mycompany.com
    routes:
      - application-name: myapp
        paths:
          - \/api\/v1\/user\/\w+\/.*
          - \/api\/v1\/stat\/\w+\/.*
```
{% endtab %}
{% endtabs %}

As you can see:

* You can specify **multiple routers**
* You can specify **multiple routes to different applications of the same project**
* You can define **multiple paths**

{% hint style="info" %}
Any other applications of the same project can create rules for any applications
{% endhint %}

{% hint style="success" %}
Qovery takes care about duplicated routes and deny the latest created one to avoid unattended override
{% endhint %}

