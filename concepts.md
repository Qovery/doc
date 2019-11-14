---
description: Know more how Qovery works
---

# Concepts

We recommend to start with the [Quickstart](quickstart/sign-up/) if you want to start quickly.

In this page, you'll find information explaining how [Qovery](https://www.qovery.com) works in details.

The main Qovery requirement is **Git**. As you \(developer\) are already using it to manage your application code. Qovery project's configuration is driven entirely by YAML files into your Git repository.

The [Services](services-1/network/) and [Extending](extending-qovery/branches.md) Qovery sections covers those in more detail and can serve as both tutorial and quick-reference.

Qovery supports the well known [**Docker**](https://www.docker.com/) **containers** technology and a number of different [Databases](services-1/databases/) and other services \(available in [Services](services-1/network/) section\).

Finally, Qovery is really fast to set up and perfectly integrate with your Git environment.

Our promise is simple:

{% hint style="success" %}
**If your container can locally run, Qovery makes it running in the Cloud at scale.**
{% endhint %}

## Git Driven Infrastructure

Qovery automatically manages everything your application needs in order to run. That means **you view your infrastructure dependencies as part of your application**. As well, **you version-control it** as part of your application.

### Simple Declarative Infrastructure <a id="infrastructure-as-code"></a>

Qovery covers not only all of your hosting needs but also **most of your DevOps needs**. It covers the application life-cycle **from development to production stage**. Ensuring as well the application is always healthy and **scales it automatically** when more workload come.

You only need to:

1. Write your code
2. Write the Dockerfile to build your application
3. Include Qovery YAML file that specify your desired infrastructure
4. Commit it to Git
5. Push it

That's it, **you don't need to setup anything manually**. Everything like the web server, the database, the CDN, the object storage etc... will be setup and available automatically.

### Branches

{% hint style="info" %}
**Every branch you push is a fully independent environment-complete**
{% endhint %}

As a developer, for developing or testing purpose, have you never been annoyed by being **not able to get a testing environment similar to production**? 99,99% of the time, the answer is **Yes**!

That's why on any [branches](extending-qovery/branches.md), you'll get a copy of your dependencies \(database, search index, object storage...\).

You can use these concepts to replicate a traditional development/staging/production workflow or even to **give every feature its own effective staging environment before merging to production** \(empowering you to use git-flow like methodologies even better\). You could also have an intermediary integration branch for several other branches.

A dedicated generated URL will be provided to those specific branches. This to get something as simple as:

{% hint style="success" %}
**What my application/site looks like locally is what I'll get in production...every time.**
{% endhint %}

Qovery respects the structure of branches. It's entirely up to you.

## Full Stack management

Managing your full stack internally gives Qovery some unique features:

1. **Unified Environment:** All of your services \(MySQL, ElasticSearch, MongoDB, etc...\) are managed inside the cluster and included in the price, with no external single-points-of-failure. When you back up an environment, you get a fully consistent snapshot of your whole application.
2. **Multi-Services & Multi-App:** You can deploy multiple applications \(for example, in a microservice-based architecture\), using multiple data backends \(MySQL, Postgres, Redis etc..\) written in multiple frameworks \(Spring + NodeJS + Flask, for example\) in multiple languages, all in the same cluster.
3. **Full Cluster Cloning Technology:** The full production cluster can be cloned in under a minute to create on-the-fly, ephemeral development environments that are a byte-level copy of production.
4. **Fail-Proof Deployments:** Every time you test a new feature, you also test the deployment process.
5. **Continuous Deployment from the Start:** Everything is build-oriented, with a consistent, repeatable build process, simplifying the process of keeping your application updated and secure.

