---
description: Regularly check your application health state
---

# Monitoring

One of the Qovery goal is to ensure your application is working well and do what is necessary if it's not the case.

In order to **get a better monitoring for your application**, you have to provide a dedicated check to your application.

{% hint style="warning" %}
**Qovery strongly advise to create an** [**application ready check**](monitoring.md#application-ready-check) **to enhance the support of your application**
{% endhint %}

## Standard check

The standard check is the way for Qovery to know when your application is started. 

{% hint style="success" %}
By default, Qovery **automatically** perform TCP checks to the declared [private port\(s\)](../../services/network/#private-access)
{% endhint %}

## Application ready check

As soon as the declared private ports are open or http check is working, incoming traffic is routed to application. **This can lead to timeouts or errors if the application is not fast enough to be ready to serve data/traffic**. That's why you need an Application ready check.

{% hint style="warning" %}
**Application ready check is the best way to ensure your application is 100% ready to serve traffic**
{% endhint %}



## Change start time delay

You may need to change the start time delay parameter if your application takes a long time to start.

{% hint style="info" %}
By default, application have 30s to boot
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

