---
description: Use containers to build and package your own application
---

# Getting started

To show you how **Qovery is simple and fast**, here is a sample project to run an application.

## Fork a sample application

Fork a [Qovery sample application \(https://github.com/Qovery/simple-example.git\)](https://github.com/Qovery/simple-example.git) by **clicking on the Fork button**:

![](../.gitbook/assets/github_fork.png)

Once done, clone your forked repository:

```bash
$ git clone git@github.com:<your-github-nickname>/simple-example.git
$ cd simple-example
```

In this repository, you'll find an already existing [Dockerfile](../services/applications/dockerfile.md), able to build and run the application.

## Qovery initialization

In order to be able to deploy this application through Qovery, we have to initiate the configuration file:

```text
$ qovery init
Reply to the following questions to initialize Qovery for this application
For more info: https://docs.qovery.com

➤ Enter the project name: my-project

➤ Choose the region where you want to host your project and applications:
0. none
1. aws/eu-west-3
➤ Your choice: 1

➤ Enter the application name [default: simple-example]:
unexpected newline

➤ Do you need a database? (PostgreSQL, MySQL, MongoDB, ...) (y/n) [default=n]: n

!!!IMPORTANT!!!
Qovery needs to get access to your git repository
https://github.com/apps/qovery/installations/new/permissions?target_id=XXXXXX

➤ Would you like to open the link above? (y/n) [default=n]: y

!!!IMPORTANT!!!
1/ Commit and push the ".qovery.yml" file to get your app deployed
➤ Run: git add .qovery.yml && git commit -m "add .qovery.yml" && git push -u origin master

2/ Check the status of your deployment
➤ Run: qovery status

Enjoy! 👋
```

In your current directory, you now have a **".qovery.yml" file describing the desired configuration** you've just asked for:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
qovery:
  key: ****************************
application:
  name: simple-example
  project: my-project
  publicly_accessible: true
routers:
- name: main
  routes:
  - application_name: simple-example
    paths:
    - /*
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Commit** the .qovery.yml configuration file to save your changes
{% endhint %}

## Deploy

Are you ready to deploy?

```bash
git push
```

 That's it!!!

{% hint style="info" %}
**We strongly encourage you to always dedicate a commit for Qovery configuration change \(in order to simplify possible rollback\)**
{% endhint %}

## Deployment status

To know what's the status of your deployment and project info, run the Qovery status command:

```bash
$ qovery status

* External DNS name               : myexample.qovery.io
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

## Code a new feature

As soon as you want to develop a new feature in your code, create a new branch!

{% hint style="info" %}
**A new branch will spawn a dedicated \(production replicated\) environment for you**
{% endhint %}

To know more about it, look at the [branch dedicated page](../extending-qovery/branches.md).

## Want more?

Qovery allows you to do more by **adding new services, new functionalities and continue to simplify your developer life**.

Read the dedicated sections to know more:

* [Applications](../services/applications/)
* [Network](../services/network/)
* [Databases](../services/databases/)
* [Brokers](../services/brokers/)
* [Storages](../services/storage/)

And feel free to look at "Extending Qovery" section to **push your application at a higher level**.

