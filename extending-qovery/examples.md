---
description: Find useful examples that fit your needs
---

# Examples

You'll find here examples and usage of Qovery.

{% hint style="warning" %}
Before starting, we strongly recommend you to start with the [Quickstart](../quickstart/sign-up/)
{% endhint %}

## Simple application with database

In this example, we'll take a simple new project which needs to have:

* 1 application
* 1 database \(PostgreSQL\)
* An S3 storage

The first thing to do is to initiate qovery in the repository:

```text
$ cd <your_git_repository>
$ qovery init
```

If you do not already have your Dockerfile, one will be suggested according your repository content. Or if you already have one

