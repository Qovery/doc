---
description: How to deploy an older application and understand Qovery rollbacks
---

# Rollbacks

The deployment of an application is an easy task on Qovery. Only one commit push and the new image is built and deployed.

We'll cover in that page, how to deploy a specific version and how rollback works.

## Automated rollback

What happens if the application is not able to start \(because of a bad configuration or a bug that crashes the application at start\)?

{% hint style="success" %}
**If the application is not able to start, Qovery automatically rollback your application to the latest working one!**
{% endhint %}

In order to avoid this kind of failures, we strongly advise you to:

* Use branches to deploy your changes on a test environment first.
* Before pushing your changes, launch `qovery run` to validate the build of your Dockerfile.

## Manual rollback

Your application starts correctly but you have identified a bug and need to rollback! Easy move, you can use `qovery deploy` command.

Look how the rollback is simple. First look at the last deployments \(limited to 10\):

```bash
$ qovery deploy list
BRANCH	COMMIT DATE                  	COMMIT ID                               	COMMIT AUTHOR    	DEPLOYED 
master	2020-02-04 15:59:14 +0100 CET	e9ebe3e4f380e5ac6d7f2e9bcb2b626382b8b77d	Pierre Mavro     	✓       	
master	2020-01-27 14:48:51 +0100 CET	cd8e726d08b4ba3fa5c5cd4054a3339a5c15446a	Pierre Mavro     	        	
master	2020-01-22 18:00:01 +0100 CET	72bb69ffc7b50367cdf6bb89881117ad48cdbcff	Pierre Mavro   
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

