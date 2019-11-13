---
description: >-
  Qovery - Container as a Service for Developers | To make the developer's life
  easier
---

# Welcome

## Getting Super Powers



Becoming a super hero is a fairly straight forward process:

Qovery is a Container-as-a-Service built especially for continuous deployment. It allows you to host web applications on the cloud while making your development and testing workflows more productive.

```
$ give me super-powers
```

If you're new to Qovery, we recommend starting with the **Big Picture**, in particular [Structure](structure.md), and [Build & Deploy](build-and-deploy.md) will get you started on the right track to best leverage Qovery.

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

The main requirement of Qovery is that you use Git to manage your application code. Your project's configuration is driven almost entirely by a YAML file in your Git repository. The **Configuration** section covers those in more detail and can serve as both tutorial and quick-reference.

Once you're strong enough, save the world:

Qovery supports Docker **Container** technology and a number of different **Databases** and other services.

```bash
// Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```

Finally, Qovery is really fast to set up and perfectly integrate with your Git environment. Our principle is: Is your container running in local? Qovery makes it running in the cloud and scale.

## Git Driven Infrastructure <a id="git-driven-infrastructure"></a>

As a Container as a Service, or CaaS, Qovery automatically manages everything your application needs in order to run. That means you can, and should, view your infrastructure needs as part of your application, and version-control it as part of your application.

### Infrastructure as code <a id="infrastructure-as-code"></a>

Qovery covers not only all of your hosting needs but also most of your DevOps needs. It is a simple, single tool that covers the application life-cycle from development to production and scaling.

You only need to write your code, including a YAML file that specify your desired infrastructure, commit it to Git, and push. You don't need to setup anything manually. The web server is already setup and configured, as is any database, search engine, or cache that you specify.

Every branch you push is a fully independent environment—complete with your application code, a copy of your database, a copy of your search index, everything—and its automatically generated URL can be sent to stakeholders or to automated CI systems. It really is "what would my site look like if I merged this to production?" Every time.

You can use these concepts to replicate a traditional development/staging/production workflow or even to give every feature its own effective staging environment before merging to production \(empowering you to use git-flow like methodologies even better\). You could also have an intermediary integration branch for several other branches.

Qovery respects the structure of branches. It's entirely up to you.

### Full stack management <a id="full-stack-management"></a>

Managing your full stack internally gives Qovery some unique features:

1. **Unified Environment:** All of your services \(MySQL, ElasticSearch, MongoDB, etc...\) are managed inside the cluster and included in the price, with no external single-points-of-failure. When you back up an environment, you get a fully consistent snapshot of your whole application.
2. **Multi-Services & Multi-App:** You can deploy multiple applications \(for example, in a microservice-based architecture\), using multiple data backends \(MySQL, Postgres, Redis etc..\) written in multiple frameworks \(Spring + NodeJS + Flask, for example\) in multiple languages, all in the same cluster.
3. **Full Cluster Cloning Technology:** The full production cluster can be cloned in under a minute to create on-the-fly, ephemeral development environments that are a byte-level copy of production.
4. **Fail-Proof Deployments:** Every time you test a new feature, you also test the deployment process.
5. **Continuous Deployment from the Start:** Everything is build-oriented, with a consistent, repeatable build process, simplifying the process of keeping your application updated and secure.

