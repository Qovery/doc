---
description: Build and generate Golang application container
---

# Go



* **Go**: build the application with dependencies \(using dep\) and get the compiled binary to add into a new dedicated slim image

\*\*\*\*

{% tabs %}
{% tab title="Go Modules" %}
```

```
{% endtab %}

{% tab title="Dep" %}
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

{% tab title="Glide" %}
```

```
{% endtab %}
{% endtabs %}

## 

