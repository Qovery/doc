# Dockerfile

## How to build your container application

Building your own application is something every developer knows how to. Building a container with the application inside is not more complex.

At Qovery we're using the well known Dockerfile to build [multi stage](https://docs.docker.com/develop/develop-images/multistage-build/) containers. You can see in the examples below 

Here are some Dockerfiles examples to **add into the root directory of your git repository**:

* **Java**: gradle installation to build application and get the uber Jar \(fat Jar\)  to add into a new dedicated slim image
* **Python**: build dependencies from requirements.txt and get the applications + its dependencies into a new dedicated slim image
* **Go**: build the application with dependencies \(using dep\) and get the compiled binary to add into a new dedicated slim image

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



