---
description: Deploy your application in production
---

# Deploy

Are you ready to deploy?

```bash
git push
```

 That's it!!!

{% hint style="info" %}
**We strongly encourage you to always dedicate a commit for Qovery configuration change \(in order to simplify possible rollback\)**
{% endhint %}

## Deployment status

To know what's the status of your deployment and project info, run this command:

```bash
$ qovery status

* External DNS name               : <myapplicationid>.qovery.io
* SSL/TLS enabled                 : https://myexample.qovery.io
* Current deployed version        : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
* In progress deployment          : b0b03ab (Ada Lovelace) / 75% done
* Pending deployments in the pipe : 0
* Total deployments today         : 3
* Total rollback today:           : 0
```

{% hint style="success" %}
Your application is automatically available on https://myexample.qovery.io
{% endhint %}

You can also get those information from the Web interface of course. To know more about deployments process, you can read the [deployment strategies](../extending-qovery/deployments-strategies.md) section.

## Code a new feature

As soon as you want to develop a new feature in your code, create a new branch!

{% hint style="info" %}
**A new branch will spawn a dedicated \(production replicated\) environment for you**
{% endhint %}

To know more about it, look at the [branch dedicated page](../extending-qovery/branches.md).

