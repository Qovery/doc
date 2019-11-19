---
description: Choose the way you want your application will be upgraded
---

# Upgrade strategies

This page explains how you can perform application upgrades. Qovery handles the automatic scaling of your application. But depending on how is made your application and what kind of data it manages, you may want to customize the upgrade procedure.

This to **avoid your application unexpected behavior,** when you're trying to upgrade the current running version. Several options exists, you can **choose the one you want per application**.

## Ramped \(default\)

The Ramped strategy **slowly replace old application version by the new one**. During the deployment, the number of old container version decrease. And the new version increase, until the correct number of container to support your workload is reached.

{% hint style="info" %}
The Ramped strategy implies **having 2 different application versions** \(the old one and the new one\) **running at the same time** during the upgrade strategy.
{% endhint %}

| Pros | Cons |
| :--- | :--- |
| Upgrade is **slowly and safely** released | Application **should be able to live properly with 2 different version** during the upgrade process |
| Convenient for stateful application | You can't control incoming traffic |

You can either customize the speed and limits of the upgrade strategy in the Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
app:
  name: myapp
  project: test
  upgrade-strategy:
    type: ramped
    max-unavailable: 25%
    max-surge: 25%
```
{% endtab %}
{% endtabs %}

As you can see here, there are 2 interesting options:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Options name</th>
      <th style="text-align:center">Default</th>
      <th style="text-align:left">Comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">max-unavailable</td>
      <td style="text-align:center">25%</td>
      <td style="text-align:left">
        <p>Set the <b>maximum unavailable container at a time</b> during the upgrade.
          It can be a percentage or an integer</p>
        <p>Eg. you have 10 running containers and want to create new only 1 by 1,
          you have to set 1 here</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">max-surge</td>
      <td style="text-align:center">25%</td>
      <td style="text-align:left">How maximum containers can be added at once</td>
    </tr>
  </tbody>
</table>## **Recreate**

The Recreate strategy is the **simplest one**. As soon as you want to upgrade to a new version, it will stop the current deployed containers. Then, when no one remains, it will deploy the new container version.

| Pros | **Cons** |
| :--- | :--- |
| **Application state are entirely renewed**. Only one application version run at a given time. | The **downtime depends on the shutdown and boot duration** of the application |

Here is the strategy configuration to set in the Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
app:
  name: myapp
  project: test
  upgrade-strategy:
    type: recreate
```
{% endtab %}
{% endtabs %}

## Blue/Green

The blue/green strategy allows to **quickly switch from one version to another in an instant**. It starts as many new containers version \(green\) as there are already started old container version \(blue\). Then, when all the containers \(green\) are started, all the traffic is redirected at once to the green containers. The blue containers are then stopped.

| Pros | Cons |
| :--- | :--- |
| Instant rollout | Requires to double the resources |
| Avoid API/Application versioning issue | Perfect application testing is required before going to production |

Here is the strategy configuration to set in the Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
app:
  name: myapp
  project: test
  upgrade-strategy:
    type: blue-green
```
{% endtab %}
{% endtabs %}

