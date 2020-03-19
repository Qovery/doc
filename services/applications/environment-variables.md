---
description: Use default built-in variables and add your custom ones
---

# Environment variables

Qovery supports environment variables to help you to **find and use** useful information regarding your application and the environment related to your branch.

{% hint style="info" %}
**Environment variable** or **Env** name used by Qovery is different from **environment:**

* **Environment variable** or **env\(s\):** represent the environment variables
* **Environment**: is the branch name and environment designation like prod, preprod, staging, feature-branch etc...
{% endhint %}

## Levels of environment variables

There are several levels of environment variables, to provide **precedence and overrides in this order**:

| Scope | Level | Description |
| :--- | :--- | :--- |
| **BUILT\_IN** | 1 | Automatically generated variables accordingly to your configuration and will be propagated to any projects, environments and applications |
| **PROJECT** | 2 | Env variables at the project level, are shared across all environments and all applications of the current project |
| **ENVIRONMENT** | 3 | Env variables at the environment level, are shared across all applications of the same project |
| **APPLICATION** | 4 | Env variables at one one application |

{% hint style="success" %}
You can override variables, the **highest variable level win** \(application car override any other variable herited from other levels\).
{% endhint %}

## Built-In environment variables

By default, every environment will have those variables:

| Variable name | Value example | Description |
| :--- | :--- | :--- |
| QOVERY\_JSON\_B64 | &lt;base64&gt; | Current application JSON configuration encoded in base 64 |
| QOVERY\_BRANCH\_NAME | master | Git branch name |
| QOVERY\_IS\_PRODUCTION | true/false | Your defined production branch |

## Naming convention

**For any added services \(database, brokers, storage\)**, you will get additional built-in variables. There is a naming convention for this:

```text
QOVERY_<SERVICE_TYPE>_<NAME>_<SPEC>
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
  name: my-pg
```
{% endtab %}
{% endtabs %}

You will automatically get those kind of variables:

| Variable name | Value example | Description |
| :--- | :--- | :--- |
| QOVERY\_**DATABASE**\_**MY\_PG**\_**NAME** | my-postgresql | Name of your PostgreSQL database |
| QOVERY\_**DATABASE**\_**MY\_PG**\_**HOST** | &lt;host&gt;.amazonaws.com | PostgreSQL host address |
| QOVERY\_**DATABASE**\_**MY\_PG**\_**USERNAME** | username | PostgreSQL username |
| QOVERY\_**DATABASE**\_**MY\_PG**\_**PASSWORD** | password | PostgreSQL password |
| ... | ... | ... |

## List environment variables

For a given application, you can list the current variables:

```text
$ qovery application env list
SCOPE        KEY                                                   VALUE
BUILT_IN     QOVERY_BRANCH_NAME                                    feature_a
BUILT_IN     QOVERY_IS_PRODUCTION                                  false
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_PASSWORD        xxxxxxxxxxxxxxxxxxxx
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_USERNAME        superuser
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_PORT            5432
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_FQDN            your.fqdn.id.rds.amazonaws.com
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_HOST            your.host.id.rds.amazonaws.com
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_CONNECTION_URI  postgresql://user:pass@your.fqdn.id.rds.amazonaws.com:5432/postgres
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_VERSION         11.5
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_TYPE            POSTGRESQL
BUILT_IN     QOVERY_DATABASE_MY_POSTGRESQL_3498225_NAME            my-postgresql-id
PROJECT      my_custom_project_env                                 my_project_value
ENVIRONMENT  DRY_RUN                                               true
APPLICATION  enable_feature_a                                      true
```

But you can also do it for project and environment:

```text
$ qovery project env list
$ qovery environment env list
```

## Custom environment variables \(Envs\)

You can manage by your own the variables associated to projects, environments and applications. We've previously seen how to [list them](environment-variables.md#list-environment-variables). We're now going to see how to add and remove them.

{% hint style="warning" %}
Ensure you're in the wished application directory and on the correct branch \(environment\) before updating variables
{% endhint %}

### Add environment variable \(env\)

To add variables, first define at [which scope](environment-variables.md#levels-of-environment-variable) you want to add your variable. Then use `add` command. Here are examples:

```bash
$ qovery project env add env_name value
$ qovery environment env add env_name value
$ qovery application env add env_name value
```

Once done, you can [list them](environment-variables.md#list-environment-variables).

### Override environment variable \(env\)

As described in the [levels' section](environment-variables.md#levels-of-environment-variable), you can override existing variables.

For example, for a given environment, we want to override an application env. **We simply have to add an env with the same key name**.

{% hint style="success" %}
Even BUILT-IN environment variable can be overridden
{% endhint %}

### Environment variable alias \(env\)

You can create an environment variable alias from another environment variable

```text
$ qovery application env add DB_HOST $QOVERY_DATABASE_MY_POSTGRESQL_HOST
```

### Delete environment variable \(env\)

Let's look at what we want to delete by listing environment variables:

```text
$ qovery application env list                                                                                                                                                               Fri Jan 31 17:51:19 2020
SCOPE        KEY          VALUE
APPLICATION  my_env_name  my_value
```

Here we're going to remove the environment variable named `my_env_name` in the application's scope:

```text
$ qovery application env delete my_env_name
ok
```

{% hint style="info" %}
Only **non** BUILT-IN environment variables can be deleted
{% endhint %}

