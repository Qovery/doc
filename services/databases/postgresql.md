---
description: 'PostgreSQL is a high-performance, standards-compliant relational SQL database.'
---

# PostgreSQL

[PostgreSQL](https://www.postgresql.org/) is a powerful, open source **object-relational database system** with over 30 years of active development that has earned it a strong reputation for **reliability, feature robustness, and performance**.

## Add a new database instance to an existing application

To **add a new dedicated PostgreSQL instance** to an existing application, you can use update the configuration file by adding these lines:

{% tabs %}
{% tab title=".qovery.yml" %}
```bash
application:
...
databases:
- type: postgresql
  version: "11.5"
  name: my-postgresql-6132005
```
{% endtab %}
{% endtabs %}

* **name**: the name of your postgres database
* **version**: the versions of PostgreSQL
* **type**: the database engine

## Access to an instance

The following samples give you the way to access all necessaries information to access your PostgreSQL instance.

{% tabs %}
{% tab title="NodeJS" %}
```javascript
const { Pool } = require('pg');
const { Qovery } = require('qovery');

const dbConfiguration = new Qovery().databaseConfiguration();

const pool = new Pool({
    host: dbConfiguration.host,
    port: dbConfiguration.port,
    user: dbConfiguration.user,
    password: dbConfiguration.password,
    database: 'test', 
});

// your code
```
{% endtab %}

{% tab title="Java" %}
```java
package com.qovery.languages.sample;

import com.qovery.Qovery;
import com.qovery.DatabaseConfiguration;

import javax.sql.DataSource;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;

public class PostgreSQLSample {

    @Override
    public String get() {
        // Create a new config object to ease reading the Qovery environment variables.
        // You can alternatively use getenv() yourself.
        Qovery qovery = new Qovery();

        // "my-super-instance" is the database name instance to access
        DatabaseConfiguration config = qovery.getDatabaseConfiguration("my-super-instance");
        
        // your database name
        String databaseName = "test";

        // connection URI string
        String uri = "jdbc:postgresql://" + 
            config.getHost() + ":" + 
            config.getPort() + "/" + 
            databaseName;

        // Connect to the database
        try (Connection connection = DriverManager.getConnection(uri, config.getUsername(), config.getPassword())) {
            // your code here :)
        } catch (SQLException exp) {
            throw new RuntimeException("An error when execute PostgreSQL", exp);
        }
    }
}
```
{% endtab %}
{% endtabs %}

## Get instance status

To know more about your instance status, you can do it this way:

```bash
$ qovery status
...
Databases
name                   status  type        version  endpoint           port  username   password  application
my-postgresql-3498225  LIVE    POSTGRESQL  11.5     xxx.amazonaws.com  5432  user       password  client-example-postgresql
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

## Restore \(coming soon\)

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

