---
description: List of all provided SDKs to easily access to Qovery resources
---

# SDKs

Qovery provides SDKs for most popular languages. The end goal of SDKs is to make the usage of Qovery services very easy for your favorite language. 

{% hint style="info" %}
Qovery SDKs are wrappers around Qovery API to get services \(databases, brokers..\) configuration information like credentials, host, port and much more.
{% endhint %}

Here is the list of supported languages:

* [NodeJS](sdks.md#nodejs)
* [Python](sdks.md#python)
* [PHP](sdks.md#php)
* [Java](sdks.md#java)
* [Go](sdks.md#go)
* [Other](sdks.md#other)

{% hint style="info" %}
If your language is not supported yet please use the "**Other**" way
{% endhint %}

## NodeJS

Minimum supported version:

* 6
* 8
* 10

```bash
npm install qovery
```

[Checkout available versions](https://github.com/Qovery/qovery-javascript-sdk)

## Python

Supported versions:

* 3.x

```bash
pip install qovery
```

[Checkout available versions](https://github.com/Qovery/qovery-php-sdk)

## PHP

Supported versions:

* 5.6+

```bash
composer require qovery
```

[Checkout available versions](https://github.com/Qovery/qovery-php-sdk)

## Java

Supported versions:

* 1.8+

{% tabs %}
{% tab title="pom.xml" %}
```markup
<dependency>
    <groupId>com.qovery</groupId>
    <artifactId>client</artifactId>
    <version>1.0.0</version>
</dependency>
```
{% endtab %}

{% tab title="build.gradle" %}
```
compile group: 'com.qovery', name: 'client', version: '1.0.0'
```
{% endtab %}
{% endtabs %}

[Checkout available versions](https://github.com/Qovery/qovery-java-sdk)

## Go

Supported versions:

* 1.10+

```bash
import "github.com/Qovery/qovery-go-sdk"
```

