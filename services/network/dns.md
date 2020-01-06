---
description: Manage your DNS
---

# DNS

A DNS \(Domain Name System\) is **automatically generated** on deployed applications requesting a [public access](./#public-access). This allows you to get a simple way to access your application. You'll get one DNS name per branch as well.

## Qovery DNS \(default\)

There is **nothing to do, as soon as you define a public port to your application** in the .qovery.yml file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  publicly_accessible: true
```
{% endtab %}
{% endtabs %}

To check the DNS name, you can do it through CLI:

```bash
$ qovery status

Environment
branch  status  endpoints                    applications  databases  brokers  storage
master  LIVE    https://xxxxxxxx.qovery.io   1             0          0        0

Applications
name            status  databases  brokers  storage
myapp-test      LIVE    0          0        0
```

You can also see it from the Web interface.

## Custom DNS

You can define custom DNS name with your company name.

{% hint style="info" %}
**Custom DNS name is only activated on master branch**
{% endhint %}

Simply add "dns" line like this in the .qovery.yml file: 

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test

network:
  dns: myapp.mydomain.name
  public-port: 80
```
{% endtab %}
{% endtabs %}

Then commit and push to apply this new change.

Finally you have to **configure a "A" record name to your DNS registrar** \(or the entity in charge of your domain name\). To get the IP address to point your "A" record to, use the Qovery CLI:

```bash
$ qovery status

Environment
branch  status  endpoints                    applications  databases  brokers  storage
master  LIVE    https://myapp.mydomain.name  1             0          0        0

Applications
name            status  databases  brokers  storage
myapp-test      LIVE    0          0        0
```

The record name should be configured to point to the IP address like:

`myapp.mydomain.name -> ip_address`



