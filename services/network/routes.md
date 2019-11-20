---
description: Add routes to your application
---

# Routes



{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: my-backend-api
  project: test
...
routers:
  - name: backend-router
    dns: api.toto.io
    routes:
      - application-name: myapp
        paths:
          - /api/v1/user/\w+/.*
          - /api/v1/stat/\w+/.*
```
{% endtab %}
{% endtabs %}



