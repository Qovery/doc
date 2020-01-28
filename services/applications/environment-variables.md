---
description: Use default variables and add your custom ones
---

# Environment variables

By default, Qovery provides environment variables to help you to find useful information. You can also add your environment variable if you need. This page will cover all those aspects.

## Default environment variables

By default, any configuration will have at least those variables:

| Variable name | Value example | Description |
| :--- | :--- | :--- |
| QOVERY\_BRANCH\_NAME | master | Git branch name |
| QOVERY\_IS\_PRODUCTION | true/false | Your defined production branch |

### Naming convention

For any added services \(database, brokers, storage\), you will get additional default variables. There is a naming convention for this:

```text
QOVERY_<SERVICE_TYPE>_<NAME>
```

Let's take a simple example with a database. You configuration should looks similar to this one:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  ...
databases:
- type: postgresql
  version: "10.10"
  name: my-postgresql
```
{% endtab %}
{% endtabs %}

You will automatically get those variables:

| Variable name | Value example | Description |
| :--- | :--- | :--- |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_NAME | my-postgresql | Name of your PostgreSQL database |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_TYPE | true/false | Your defined production branch |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_VERSION | 10.10 | PostgreSQL version |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_URI | postgresql://&lt;username&gt;:&lt;password&gt;@&lt;host&gt;:&lt;port&gt;/&lt;db\_name&gt; | PostgreSQL URI address |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_HOST | &lt;host&gt;.amazonaws.com | PostgreSQL host address |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_FQDN | &lt;host&gt;.amazonaws.com | PostgreSQL fqdn address |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_PORT | 5432 | PostgreSQL port |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_USERNAME | username | PostgreSQL username |
| QOVERY\_DATABASE\_MY\_POSTGRESQL\_PASSWORD | password | PostgreSQL password |

## Custom environment variables

 

