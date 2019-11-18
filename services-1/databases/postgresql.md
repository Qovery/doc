---
description: 'PostgreSQL is a high-performance, standards-compliant relational SQL database.'
---

# PostgreSQL

[PostgreSQL](https://www.postgresql.org/) is a powerful, open source **object-relational database system** with over 30 years of active development that has earned it a strong reputation for **reliability, feature robustness, and performance**.

## Add a new instance to an existing application

To **add a new dedicated PostgreSQL instance** to an existing application, you can use Qovery CLI to do it:

```bash
$ qovery add database

➤ Choose the database instance you want to add: 1
1. PostgreSQL
2. MongoDB
...

➤ Set the instance name: my-super-instance

➤ Estimated PostgreSQL data size in GiB (default: 10): 20

➤ Please choose the kind of performances you need: 3
1. Tiny   : 1 vCPU / 2GiB Ram
2. Small  : 2 vCPU / 8Gib Ram
3. Medium : 4 vCPU / 16GiB Ram
4. Big    : 8 vCPU / 32GiB Ram
5. Huge   : 16 vCPU / 64GiB Ram
c. Custom Mode

✓ Your Qovery configuration file has been successfuly updated (.qovery.yml)!

➤ Commit into your repository and push it to get this deployed.
```

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
$ qovery status database

✓ my-super-instance:
* Branch  : master (Production)
* Health  : healthy
* Type    : PostgreSQL
* Version : 11.4
* Size    : 20GiB
* Kind    : Medium (4 vCPU / 16GiB Ram)
```







