---
description: Add security to your website
---

# https \(SSL/TLS\)

The SSL/TLS certificates are mandatory to get a **secure** website.

## Get a certificate

In order to get a SSL/TLS certificate, **you simply have to set the "public-port" parameter to "443"** in the .qovery.yml file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  private-port: 8080
  public-port: 443
```
{% endtab %}
{% endtabs %}

Then commit and push to apply this new change.

Then, to get the status of your application from the CLI to get the https URL:

```bash
$ qovery status

* External DNS name        : <myapplicationid>.qovery.io
* SSL/TLS enabled          : https://<myapplicationid>.qovery.io
* Current deployed version : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```

You can also see it from the Web interface.

