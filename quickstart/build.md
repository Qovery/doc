---
description: Use containers to build and package your own application
---

# Build container

Building your application is something every developer knows how to. Building a container with the application inside is not more complex but not every developers are familiar with. In order to help developers, this page provides examples on how to manage it.

## Generate a Dockerfile

At Qovery we're using the well known Dockerfile to build multi staged containers.

From the Qovery cli, you can generate a Dockerfile. Here is how to:

```bash
$ cd <your_git_repository>
$ qovery init

➤ Java application detected, do you want to generate a Dockerfile for it (y/n): y
✓ Dockerfile generated in the Git root directory
```

{% hint style="info" %}
No Dockerfile will be generated if one already exists
{% endhint %}

## Define the build and run process

We'll need to first build the application and then create a dedicated minimal container with the application embedded.

![](../.gitbook/assets/q-quickstart-build.png)

Here is an example of a Dockerfile to build a Java application:

{% tabs %}
{% tab title="Dockerfile" %}
```bash
# Build your application with this image called "build"
FROM openjdk:11 AS build
# Add the required packages
RUN apk -U add bash
# Add your specifc dependencies
RUN cd /usr/local/bin && \
    wget https://services.gradle.org/distributions/gradle-6.0-bin.zip && \
    /usr/bin/unzip gradle-5.6-all.zip && \
    ln -s /usr/local/bin/gradle-5.6/bin/gradle /usr/bin/gradle && \
    mkdir -p /app
# Copy your code in the build container and move into it
COPY . /app
WORKDIR /app
# Build your application
RUN gradle build

# The container which will run
FROM openjdk:11-alpine
# Get the build artifact (can be a folder)
COPY --from=build /app/build/libs/app.jar /app.jar
# Set specific environment variables
ENV JAVA_OPTS=""
# Command to run your application
CMD exec java $JAVA_OPTS -jar /app.jar
```
{% endtab %}
{% endtabs %}

1. **Build**: The first part \(from the first line to 15\) represent the dependencies and requirements in order to **build the application**. The application final form is called an **artifact** available in the `/app/build/libs/app.jar` directory.
2. **Run**: The second part \(from line 18 to last\) represent the content of the container that will **run in production** \([or for a specific branch](../extending-qovery/branches.md)\). It retrieves the artifact from the build part and store it in the container.

{% hint style="danger" %}
**For security reasons**, for we strongly advise you to:

1. Use [Docker Official Images](https://hub.docker.com/search/?q=&type=image&image_filter=official)
2. Use the lightest image as possible such as scratch or alpine
{% endhint %}

## Validate your Dockerfile

You can validate your Dockerfile by running a build on your machine.

{% hint style="info" %}
You need to have [Docker binary installed](https://docs.docker.com/install/) on your computer to validate the build
{% endhint %}

You simply have to run:

```bash
qovery build
```

or by using Docker:

```bash
docker build .
```

## Other references

* [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
* [Multi stages Dockerfiles](https://docs.docker.com/develop/develop-images/multistage-build/)

