---
description: Manage your DNS
---

# DNS

A DNS \(Domain Name System\) is **automatically generated** on deployed applications requesting a [public access](./#public-access). This allows you to get a simple way to access your application. You'll get one DNS name per branch as well.

There is **nothing to do, as soon as you define a public port to your application** in the .qovery.yml file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
app:
  name: myapp
  private-port: 8080
  public-port: 80
  project: test
```
{% endtab %}
{% endtabs %}

Then commit and push to apply this new change.

To check the DNS name, you can do it through CLI:

```bash
$ qovery status

* External DNS name               : <myapplicationid>.qovery.io
* Current deployed version        : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```

You can also see it from the Web interface.

## Custom DNS

You can define custom DNS name with your company name.

{% hint style="warning" %}
**SSL/TLS is not supported on custom DNS name**
{% endhint %}

{% hint style="info" %}
**Custom DNS name is only activated on master branch**
{% endhint %}

Simply add "dns" line like this in the .qovery.yml file: 



{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
app:
  name: myapp
  dns: myapp.mydomain.name
  private-port: 8080
  public-port: 80
  project: test
```
{% endtab %}
{% endtabs %}

Then commit and push to apply this new change.

Finally you have to **configure a "A" record name to your DNS registrar** \(or the entity in charge of your domain name\). To get the IP address to point your "A" record to, use the Qovery CLI:

```bash
$ qovery status

* External DNS name               : myapp.mydomain.name / <ip_address>
* Current deployed version        : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```

The record name should be configured to point to the IP address like:

`myapp.mydomain.name -> ip_address`

