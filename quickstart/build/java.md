---
description: Build and generate Java application container
---

# Java



* **Java**: gradle installation to build application and get the uber Jar \(fat Jar\)  to add into a new dedicated slim image



\*\*\*\*

{% tabs %}
{% tab title="Gradle" %}
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

{% tab title="Maven" %}
```

```
{% endtab %}
{% endtabs %}

## 

