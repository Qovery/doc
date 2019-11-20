---
description: Add routes to your application
---

# Routes



{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
...
routes:
  - router-name: router1
    dns: myapplication.qovery.io
    - application-name: app1
      - path: /api/v1/\w+/user/.*
      - path: /.*
    - application-name: app2
      - path: /service/.*
```
{% endtab %}
{% endtabs %}



