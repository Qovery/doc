---
description: Build and generate Python application container
---

# Python



* **Python**: build dependencies from requirements.txt and get the applications + its dependencies into a new dedicated slim image

\*\*\*\*

{% tabs %}
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
{% endtabs %}

## 

