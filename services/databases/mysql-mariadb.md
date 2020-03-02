---
description: 'MySQL is a high-performance, relational SQL database.'
---

# MySQL

[MySQL](https://www.mysql.com/) is the world's most popular open source database. Whether you are a fast growing web property, technology ISV or large enterprise, MySQL can cost-effectively help you deliver high performance, scalable database applications.

## Add a new database instance to an existing application

To **add a new dedicated MySQL instance** to an existing application, you can use update the configuration file by adding these lines:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
...
databases:
- type: mysql
  version: "8.0"
  name: my-mysql
```
{% endtab %}
{% endtabs %}

* **name**: the name of your MySQL database
* **version**: the versions of MySQL
* **type**: the database engine

## Access to an instance

The following samples give you the way to access all necessaries information to access your MySQL instance.

{% tabs %}
{% tab title="NodeJS" %}
```javascript
const { Pool } = require('mysql');
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
        String uri = "jdbc:mysql://" + 
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
name      status  type    version  endpoint           port  username   password  application
my-mysql  LIVE    MYSQL   8.0      xxx.amazonaws.com  3306  user       password  client-example-mysql
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

You can change the window very easily \(use 24h format\):

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  ...
databases:
  - name: my-mysql
    type: mysql
    backup-window: 21-23
```
{% endtab %}
{% endtabs %}

As described here, the backup will occur between 9PM and 11PM.

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

➤ Please confirm by typing the database instance name: my-mysql

✓ Backup successfuly created
✓ Backup as successfuly been restored (23/11/2019 - 22h)
```

