---
description: Regularly check your application health state
---

# Health monitoring

One of the Qovery goal is to ensure your application is working well. Qovery manage the application failure!

In order to **get a better availability of your application**, we need to better monitor it. To do so, you have to provide a dedicated monitoring way that understand well your application.

{% hint style="warning" %}
**Qovery strongly advise to create a** [**Ready check**](monitoring.md#application-ready-check) **to significantly enhance the availability of your application**
{% endhint %}

## Standard check

The standard check is used to know when your application is started. For this, Qovery use the private declared ports.

{% hint style="success" %}
By default, Qovery **automatically** perform TCP checks to the declared [private port\(s\)](../../services/network/#private-access)
{% endhint %}

{% hint style="info" %}
Standard check is performed every 10 seconds
{% endhint %}

**If no ports are declared**, Qovery assume the application works until exit \(when the application PID dies\).

## Ready check

As soon as the declared private ports are open, incoming traffic is routed to application. **This can lead to timeouts or errors if the application is not fast enough to be ready to serve data/traffic**. That's why you need a Ready check.

{% hint style="success" %}
**Ready check is the best way to ensure your application is 100% ready to serve traffic**
{% endhint %}

To use a Ready check, you have 2 solutions:

1. \*\*\*\*[**http check**](monitoring.md#http-check): simplest way to validate your application
2. \*\*\*\*[**Command check**](monitoring.md#command-check): call a command/script embedded in your container

{% hint style="info" %}
Ready check is performed every 15 seconds
{% endhint %}

### http check

If you already have a web service listening for your app, you can **add a ping url**. It should **return an http code**. Otherwize, in most of the languages, you can easily create one just for it.

{% hint style="info" %}
Port should be listen to all interfaces to be reachable. You don't have to declare any private or public access to get it work
{% endhint %}

But **we recommend to perform inter-application tests to validate your application is healthy**, then **return a 200 code** when ok. If one inter-application health test fails, return a code between 400 and 499.

To enable it, add this in your Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  ready-check:
    http-url: /health
    port: 8080
```
{% endtab %}
{% endtabs %}

### Command check

To enable this check, **you have to know the command you have to run inside the container** to validate it's ready to serve traffic. Or if it's not a command, **it can be a script** containing the commands to execute in your container. The **exit command/script should be 0 when it's ready.**

To enable it, add this in your Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  ready-check:
    command: /opt/ready-check.sh
```
{% endtab %}
{% endtabs %}

## Change start time delay

You may need to change the start time delay parameter if your application takes a long time to start.

{% hint style="info" %}
**By default, application have 30 seconds to boot**
{% endhint %}

You can change it with this parameter in your Qovery configuration file \(in seconds\):

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  start-time-delay: 60
```
{% endtab %}
{% endtabs %}

