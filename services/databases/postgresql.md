---
description: 'PostgreSQL is a high-performance, standards-compliant relational SQL database.'
---

# PostgreSQL

[PostgreSQL](https://www.postgresql.org/) is a powerful, open source **object-relational database system** with over 30 years of active development that has earned it a strong reputation for **reliability, feature robustness, and performance**.

## Add a new database instance to an existing application

To **add a new dedicated PostgreSQL instance** to an existing application, you can use update the configuration file by adding these lines:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
...
databases:
- type: postgresql
  version: "11.5"
  name: my-pg
```
{% endtab %}
{% endtabs %}

* **name**: the name of your postgres database
* **version**: the versions of PostgreSQL
* **type**: the database engine

## Get access to an instance

To get the connection information of your database, you can use the CLI:

```bash
$ qovery application env list -c
  SCOPE       | KEY                                                               | VALUE     
--------------+-------------------------------------------------------------------+-----------
  BUILT_IN    | QOVERY_JSON_B64                                                   | <base64>  
  BUILT_IN    | QOVERY_BRANCH_NAME                                                | master    
  BUILT_IN    | QOVERY_IS_PRODUCTION                                              | true      
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_NAME                               | my-pg  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_TYPE                               | POSTGRESQL     
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_VERSION                            | 11.5    
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_CONNECTION_URI                     | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_CONNECTION_URI_WITHOUT_CREDENTIALS | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_HOST                               | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_FQDN                               | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_PORT                               | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_USERNAME                           | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_PASSWORD                           | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_POSTGRESSQL_DATABASE                           | POSTGRESSQL     
```

## Get instance status

To know more about your instance status, you can do it this way:

```bash
$ qovery status -c
...
  DATABASE NAME | STATUS  | TYPE       | VERSION | ENDPOINT | PORT     | USERNAME | PASSWORD | APPLICATIONS    
----------------+---------+------------+---------+----------+----------+----------+----------+-----------------
  my-pg         | running | POSTGRESQL | 11.5     | <hidden> | <hidden> | <hidden> | <hidden> | simple-example
```

## Delete a database instance

To delete a database instance, here are the 2 possible solutions:

1. **Remove it from the configuration file**, commit and push.
2. If you worked on feature branch, delete the branch and **the database instance will automatically be deleted** as well.

{% hint style="danger" %}
**Delete action will drop the services and its data!**
{% endhint %}

{% hint style="success" %}
**Backups will be kept for 1 month if you need to recover \(just in case**😉**\)**
{% endhint %}

## Backups

{% hint style="success" %}
By default, backups are made every day between 1h and 5h.
{% endhint %}

## Restore \(coming soon: [I want this feature](https://roadmap.qovery.com/c/26-restore-a-database)\)

You can restore through the CLI or the web interface.

From the CLI:

```bash
$ qovery restore <database-instance-name>

➤ Choose the version you want to restore:
  25/11/2019 - 22h
  24/11/2019 - 22h
> 23/11/2019 - 22h
  22/11/2019 - 22h
  21/11/2019 - 22h
  
✓ You're going to restore this backup: 23/11/2019 - 22h

➤ Do you want to perform a backup before restoring? (y/n): y

➤ Please confirm by typing the database instance name: my-postgres

✓ Backup successfuly created
✓ Backup as successfuly been restored (23/11/2019 - 22h)
```

