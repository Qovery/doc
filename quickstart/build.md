---
description: Use containers to build and package your own application
---

# Build container

Building your application is something every developer knows how to. Building a container with the application inside is not more complex but not every developers are familiar with. In order to help developers, this page provides examples on how to manage it.

## Generate a Dockerfile

At Qovery we're using the well known Dockerfile to build multi staged containers.

From the Qovery cli, you can generate a Dockerfile. Here is how to do with a sample project:

```bash
$ git clone git@github.com:Qovery/doc-examples.git
$ cd doc-examples/java/spring-boot
$ qovery init

➤ Java application detected, do you want to generate a Dockerfile for it (y/n): y
✓ Dockerfile generated in the Git root directory
```

{% hint style="info" %}
No Dockerfile will be generated if one already exists
{% endhint %}

