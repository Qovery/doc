---
description: Manages your environment workspaces
---

# Branches

As described in the [Qovery concepts](../concepts.md), **a new branch will spawn a dedicated \(production replicated\) environment for you**. Qovery is not limited to this and offers many more features. This page will explain them in details.

## Restrict production replicated environment \(coming soon\)

For several reasons \(cost, real usage etc...\) you may not want to have a "production-like" environment to be replicated, as soon as a new branch is created. Or at list **you want to control** it.

What you need to do, is specifying in the Qovery configuration file, a list of name or regex you want to allow:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  production-replicated-branch:
    - preprod
    - feat-.*
```
{% endtab %}
{% endtabs %}

Here, for example:

* **"preprod" branch**: will be production replicated
* **"feat-new-stuff" branch**: will be replicated
* **"mytest" branch**: won't be replicated

## Choose your "production" branch \(coming soon\)

**By default, the "master" branch is considered as the production branch**. However, you may have your own way to work with git and you want another branch name to be the "production" one.

To do so, simply update the Qovery configuration file this way:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  production-branch: prod
```
{% endtab %}
{% endtabs %}

Here, the "production" branch is called "prod".

