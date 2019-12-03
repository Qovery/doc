---
description: Let's start with a simple application
---

# Simple application

## Description

In this example, we're taking a **single simple application**. You'll **see how fast it is** to deploy it.

We'll start new project with those constraints:

| Prerequisites | Comments |
| :--- | :--- |
| 1 application | Private port on 8080 |
| Being exposed through internet on https | Public port on 443 |
| 1 single database | MySQL database instance |
| Store images on a shared storage | S3 object storage |

## Generate configuration

The first thing to do is to initiate Qovery in the repository:

```text
$ qovery init

✓ Dockerfile detected in your root directory

➤ Enter the project name: my-project

➤ Enter the application name: simple-example

➤ What port number your application ir running on? (Hit enter if none): 8080

➤ Is this port accessible from other applications of the same project? (y/n): y

➤ Would you like to expose publicly your application on https? (y/n): y

➤ Do you need any database? (y/n): y

➤ Set the instance name: my-mysql

➤ Estimated MySQL data size in GiB (default: 10): 20

➤ Please choose the performances you need: 1
1. Tiny   : 1 vCPU / 2GiB Ram
2. Small  : 2 vCPU / 8Gib Ram
3. Medium : 4 vCPU / 16GiB Ram
4. Big    : 8 vCPU / 32GiB Ram
5. Huge   : 16 vCPU / 64GiB Ram
c. Custom Mode

➤ Do you need any other database? (y/n): n

➤ Do you need any borker? (y/n): n

➤ Do you need any storage? (y/n): y

➤ Set the bucket name: images

➤ Should "images" bucket name needs to be publicly accessible? (y/n): n

✓ Your Qovery configuration file has been successfuly created (.qovery.yml)!

➤ Commit into your repository and push it to get this deployed.
```

{% hint style="info" %}
If you do not already have a Dockerfile in your repository, one will be suggested according to your repository content.
{% endhint %}

Now that you have declared your prerequisites, you can find the result in your Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: simple-example
  project: my-project

network:
  private-port: 8080
  public-port: 443
   
databases:
  - name: my-postgresql
    type: postgresql
    version: 11.4
    size: 20GiB

storage:
  - name: s3-images
    type: object-storage
    bucket: images
    public-access: no
```
{% endtab %}
{% endtabs %}

Then you have to add in your code the [Qovery SDK](../sdks.md) to easily manage the credentials part.

## Deploy

Finally, **once committed and pushed, your application will be live!!!** You can check the status and retrieve the URL like this:

```bash
$ qovery status

* External DNS name               : myexample.qovery.io
* SSL/TLS enabled                 : https://myexample.qovery.io
* Current deployed version        : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```

