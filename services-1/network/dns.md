---
description: Manage your DNS
---

# DNS

A DNS \(Domain Name System\) is **automatically generated** on deployed applications requesting a [public access](./#public-access).

There is **nothing to do, as soon as you set to your application a public port** in the .qovery.yml file:

```yaml
app:
  name: myapp
  private-port: 8080
  public-port: 80
  project: test
```

To check the DNS name, you can do it through CLI:

```bash
$ qovery status

* External DNS name               : <myapplicationid>.qovery.io
* Current deployed version        : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```

You can also see it from the Web interface.



