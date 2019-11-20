---
description: Add routes to your application
---

# Routes

Qovery allows you to manage routing to your multiple applications.

You have to create a router by simply naming it. You can optionaly request a dns name and associated routes paths to an application.

Here is an example to add in your Qovery configuration file:

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
          - /api/v1/user/\w+/.*
          - /api/v1/stat/\w+/.*
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

{% hint style="warning" %}
Qovery takes care about duplicated routes and deny the latest created one to avoid issues on the initial one
{% endhint %}

