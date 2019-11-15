---
description: Manage your DNS
---

# DNS

A DNS \(Domain Name System\) can be **automatically generated** on applications requesting a [public access](./#public-access).

There is nothing especially to do, as soon as you set your application has declared a public port \(:

```yaml
app:
  name: myapp
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



