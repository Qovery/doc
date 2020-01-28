---
description: How to deploy an older application and understand Qovery rollbacks
---

# Rollbacks

The deployment of an application is an easy task on Qovery. Only one commit push and the new image is built and deployed.

We'll cover in that page, how to deploy a specific version and how rollback works.

## Automated rollback

What happens if the application is not able to start \(because of a bad configuration or a bug that crashes the application at start\)?

{% hint style="success" %}
**Qovery automatically rollback your application to the latest working one, if it's not able to start!**
{% endhint %}

In order to avoid this kind of failures, we strongly advise you to:

* Use branches to deploy your changes on a test environment first.
* Before pushing your changes, launch `qovery run` to validate the build of your Dockerfile.

## Manual rollback

Your application starts correctly but you have identified a bug and need to rollback! Easy move, you can use `qovery deploy` command.

Look how the rollback is simple. First look at the last deployments \(limited to 10\):

```bash
$ qovery deploy list
branch  date         commit id                                 deployed
master  one day ago  cd8e726d08b4ba3fa5c5cd4054a3339a5c15446a  ✓
master  6 days ago   72bb69ffc7b50367cdf6bb89881117ad48cdbcff  𐄂
master  6 days ago   c1e788c21692d791784f85e8b525db232a944595  𐄂
master  8 days ago   ab4748c618b73f5a07b9d22e8d5cf2f4f0b6c91d  𐄂
master  2019-12-16   9f7d0d800aab92985e30fabb01c72717c93a09e1  𐄂
master  2019-12-03   cf762fd0ab4bbe45572302e374d6fa1b3256daad  𐄂
master  2019-12-03   c2dda20ed08758843cd8b592954a3a3bb3f21119  𐄂
master  2019-12-03   888cc296b6b0b17d0d6fab4572689f6524857254  𐄂
```

As you can see, our current deployment is on the commit id `cd8e726...` But now we want to rollback on the previous one, we just have to indicate the previous commit ID:

```bash
$ qovery deploy 72bb69ffc7b50367cdf6bb89881117ad48cdbcff
deployment in progress...
hint: type "qovery status --watch" to track the progression of deployment
```

As described, you can follow the status here:

```bash
$ qovery status --watch
initialization in progress 40% |████████████████                        | [32s:18s]
```

