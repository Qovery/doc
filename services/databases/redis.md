---
description: >-
  Redis is a high-performance in-memory object store, well-suited for
  application level caching.
---

# Redis

[Redis](https://redis.io/) is an open source \(BSD licensed\), in-memory data structure store, used as a database, cache and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes with radius queries and streams

## Add a new instance to an existing application

To **add a new dedicated Redis instance** to an existing application, you can use Qovery CLI to do it:

```bash
$ qovery add database

➤ Choose the database instance you want to add: 4
1. PostgreSQL
2. MongoDB
3. MySQL
4. Redis
...

➤ Set the instance name: my-super-instance

➤ Estimated Redis data size in GiB (default: 10): 20

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

The following samples give you the way to access all necessaries information to access your Redis instance.

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
* Type    : Redis
* Version : 11.4
* Size    : 20GiB
* Kind    : Medium (4 vCPU / 16GiB Ram)
```

## Delete an instance

To delete an instance, there are 2 ways to do it, depending on the scenario you are.

{% hint style="danger" %}
**Delete action will drop the services and its data!**
{% endhint %}

{% hint style="success" %}
**Backups will be kept for 1 month if you need to recover \(just in case** 😉**\)**
{% endhint %}

### Delete for all branches

If you want to **delete** a Redsi instance with **all databases and data inside** it. You simply have to **delete the corresponding Qovery configuration** in your YAML file.

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  ...
databases:
  - type: redis
    name: my-super-instance
    version: 11.4
    size: 20GiB
```
{% endtab %}
{% endtabs %}

Once done, commit and push to apply the changes.

### Delete for one branch

Once you've finished to work on a feature branch, simply delete the branch and **the instance will automatically be delete** as well.

