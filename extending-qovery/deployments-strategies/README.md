---
description: Choose the way you want your application will be upgraded
---

# Upgrade strategies

This page explains how you can perform application upgrades. Qovery handles the automatic scaling of your application. But depending on how is made your application and what kind of data it manages, you may want to customize the upgrade procedure.

This to **avoid your application unexpected behavior,** when you're trying to upgrade the current running version. Several options exists, you can **choose the one you want per application**.

## Rolling upgrade \(default\)

The rolling upgrade strategy **slowly replace old application version by the new one**. During the deployment, it waits new ones to be properly started before removing old ones.

{% hint style="info" %}
The rolling upgrade strategy implies **having 2 different application versions** \(the old one and the new one\) **running at the same time** during the upgrade strategy.
{% endhint %}

You can either customize the speed and limits of the upgrade strategy in the Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
app:
  name: myapp
  project: test
  upgrade-strategy:
    type: rolling-upgrade
    max-unavailable: 25%
    max-surge: 25%
```
{% endtab %}
{% endtabs %}

As you can see here, there are 2 interesting options:

| Options name | Comments |
| :--- | :--- |
| max-unavailable \(default: 25%\) | set the maximum unavailable container instances at a time. It can be a percentage or an integer \(eg. you have 10 running containers and want to perform only 1 by 1, you have to set 1 here\) |
| max-surge \(default 25%\) | set the maximum of containers to create at once to perform the upgrade |

## **Recreate**

\*\*\*\*

