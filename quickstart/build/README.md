---
description: Use containers to build and package your own application
---

# Build

Building your application is something every developer knows how to. Building a container with the application inside is not more complex but not every developers are familiar with. In order to help them, this page provides examples on how to do it.

## Create a Dockerfile

At Qovery we're using the well known Dockerfile to build [multi stage](https://docs.docker.com/develop/develop-images/multistage-build/) containers.

{% hint style="info" %}
You can use Qovery CLI to generate a Dockerfile templates, at the root of your git repository: `qovery-cli init`
{% endhint %}

Here are some Dockerfiles examples to **add into the root directory of your git repository:**

{% tabs %}
{% tab title="Java" %}
```bash
FROM openjdk:11 AS build
RUN apk -U add bash
RUN cd /usr/local/bin && \
    wget https://services.gradle.org/distributions/gradle-6.0-bin.zip && \
    /usr/bin/unzip gradle-5.6-all.zip && \
    ln -s /usr/local/bin/gradle-5.6/bin/gradle /usr/bin/gradle && \
    mkdir -p /app
COPY . /app
WORKDIR /app
RUN gradle build -x test


FROM openjdk:11-alpine
EXPOSE 8080
COPY --from=build /app/build/libs/app.jar /app.jar
ENV JAVA_OPTS=""

CMD exec java $JAVA_OPTS -jar /app.jar
```
{% endtab %}

{% tab title="Python" %}
```text
FROM python:3.8 AS build
RUN apt-get update && \
    apt-get install -y --no-install-recommends build-essential gcc
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
COPY . /app
WORKDIR /app
RUN pip3 install -r requirements.txt

FROM python:3.8-slim AS build-image
COPY --from=build /opt/venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
CMD exec myapp
```
{% endtab %}

{% tab title="Go" %}
```text
FROM golang:1.13 AS build
RUN apt-get update && apt-get install go-dep
# Copy the code from the host and compile it
WORKDIR $GOPATH/src/github.com/username/repo
COPY Gopkg.toml Gopkg.lock ./
RUN dep ensure --vendor-only
COPY . ./
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .

FROM scratch
COPY --from=build /app ./
CMD exec ./app
```
{% endtab %}
{% endtabs %}

To get more examples on 

## References

* [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
* [Multi stages Dockerfiles](https://docs.docker.com/develop/develop-images/multistage-build/)

