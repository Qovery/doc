---
description: Isolated environment per branch
---

# Branches and Environments

As described in the [Qovery concepts](../concepts.md), each branch can have its own isolated environment in order to work on it without impacting the others.

By default, each branch has an environment associated with it.

-&gt; schema

If a branch is created, then a new environment is created from the data of the branch from which it was created.

-&gt; schema

During a Merge from one branch to another, the environment is then deactivated and deleted.

-&gt; schema

To limit costs, it is possible to limit the creation of the environment to certain branches.

-&gt; schema

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  active_environments:
    - master
    - staging
```
{% endtab %}
{% endtabs %}

## Choose your "production" branch \(coming soon\)

By default, **the "master" branch is considered as the production branch**. However, you may have your own way to work with git and you want another branches name to be a "production" one.

To do so, simply update the Qovery configuration file this way:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  production_branches:
    - prod
```
{% endtab %}
{% endtabs %}

Here, the "production" branch is called "prod".

## What is the difference between production environment and non-production environment?

The production environment use high-availability and resiliency systems for applications and databases. We guarantee that your app will scale as you need and will be available according to the AWS SLAs.

⚠️ production environments are more expensive than non-production environments

