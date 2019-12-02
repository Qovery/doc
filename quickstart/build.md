---
description: Use containers to build and package your own application
---

# Sample project

You'll find here a sample project to quickly run an application with a Dockerfile example.

## Fork a sample project

Fork a Qovery sample project \([https://github.com/Qovery/doc-examples](https://github.com/Qovery/doc-examples)\) by **clicking on the Fork button**:

![](../.gitbook/assets/github_fork.png)

Then, clone your repository:

```bash
$ git clone git@github.com:<your-github-nickname>/doc-examples.git
$ cd doc-examples/java/spring-boot/simple-example
```

{% hint style="info" %}
No Dockerfile will be generated as one already exists
{% endhint %}

## Dockerfile example

In the repository, you'll find an existing Dockerfile with this content:

{% tabs %}
{% tab title="Dockerfile" %}
```bash
# Build your application with this image called "build"
FROM adoptopenjdk/openjdk8:alpine AS build

# Add the required packages
RUN apk update && apk upgrade && apk add bash

# Add your specifc dependencies
RUN cd /usr/local/bin && \
    wget https://services.gradle.org/distributions/gradle-5.6-all.zip && \
    /usr/bin/unzip gradle-5.6-all.zip && \
    ln -s /usr/local/bin/gradle-5.6/bin/gradle /usr/bin/gradle

# Copy your code in the build container and move into it
RUN mkdir -p /app
COPY . /app
WORKDIR /app

# Build your application
RUN gradle build -x test

# The container that will run
FROM adoptopenjdk/openjdk8:alpine-slim

EXPOSE 8080

# Get the build artifact (can be a folder)
COPY --from=build /app/build/libs/simple-example-1.0.jar /app.jar

# Set specific environment variables
ENV JAVA_OPTS=""
# Command to run your application
CMD exec java $JAVA_OPTS -jar /app.jar
```
{% endtab %}
{% endtabs %}

At Qovery we're using the well known Dockerfile to build multi staged containers. In the case you're not familiar with Dockerfiles, you can look to the [dedicated section here](../extending-qovery/dockerfile.md).

