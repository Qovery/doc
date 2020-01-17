---
description: Manage the network part
---

# Network

On your Qovery project, you can configure the way your applications are accessible from the [outside \(internet\)](./#public-access) or in a [private, dedicated and secure way](./#private-access) with other applications from the same project.

{% hint style="warning" %}
**By default the access to your application network is private. Nothing outside your project can access to your applications until you explicitly specified it.**
{% endhint %}

## Private Access

By default, exposed ports in your Dockerfile \([EXPOSE instruction](https://docs.docker.com/engine/reference/builder/#expose)\) are visible by others applications **of the same project**.

![](../../.gitbook/assets/qovery-private-network.png)

Here is an example Dockerfile with Expose:

{% tabs %}
{% tab title="Dockerfile" %}
```bash
# Build your application with this image called "build"
FROM adoptopenjdk/openjdk8:alpine AS build
RUN apk update && apk upgrade && apk add bash
RUN cd /usr/local/bin && \
    wget https://services.gradle.org/distributions/gradle-5.6-all.zip && \
    /usr/bin/unzip gradle-5.6-all.zip && \
    ln -s /usr/local/bin/gradle-5.6/bin/gradle /usr/bin/gradle
RUN mkdir -p /app
COPY . /app
WORKDIR /app
RUN gradle build -x test

# The container that will run
FROM adoptopenjdk/openjdk8:alpine-slim
# Here you need to declare your EXPOSE ports to be used
EXPOSE 8080
COPY --from=build /app/build/libs/simple-example-1.0.jar /app.jar
ENV JAVA_OPTS=""
CMD exec java $JAVA_OPTS -jar /app.jar
```
{% endtab %}
{% endtabs %}

For the moment only one port is supported.

## Public Access

To allow public access, you first need to be sure that you exposed the port \(in the Dockerfile\) as described in the "[Private Access](./#private-access)" section of this page.

![](../../.gitbook/assets/qovery-pulic-network.png)

Then add to the Qovery configuration file \(.qovery.yaml\), "publicly\_accessible" parameter to allow external access from https \(port 443\):

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  publicly_accessible: true
```
{% endtab %}
{% endtabs %}

