---
description: >-
  afka is an open-source stream-processing software platform. It is a framework
  for storing, reading and analyzing streaming data.
---

# Kafka

[Kafka](https://kafka.apache.org/) is used for building real-time data pipelines and streaming apps. It is horizontally scalable, fault-tolerant and wicked fast.

## Add a new instance to an existing application

To **add a new dedicated Kafka instance** to an existing application, you can use Qovery CLI to do it:

```bash
$ qovery add database

➤ Choose the broker instance you want to add: 2
1. RabbitMQ
2. Kafka

➤ Set the broker instance name: my-kafka

➤ Estimated RabbitMQ data size in GiB (default: 10): 20

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

The following samples give you the way to access all necessaries information to access your Kafka instance.

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
$ qovery status broker

✓ my-kafka:
* Branch  : master (Production)
* Health  : healthy
* Type    : Kafka
* Version : 11.4
* Size    : 20GiB
* Kind    : Medium (4 vCPU / 16GiB Ram)
```

## Delete a broker instance

To delete a broker instance, here are the 2 possible solutions:

1. **Remove it from the configuration file**, commit and push
2. If you worked on feature branch, delete the branch and **the broker instance will automatically be deleted** as well.

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
  - name: my-kafka
    type: kafka
    backup-window: 21-23
```
{% endtab %}
{% endtabs %}

As described here, the backup will occur between 9PM and 11PM.

## Restore

You can restore through the CLI or the web interface.

From the CLI:

```bash
$ qovery restore <broker-instance-name>

➤ Choose the version you want to restore:
  25/11/2019 - 22h
  24/11/2019 - 22h
> 23/11/2019 - 22h
  22/11/2019 - 22h
  21/11/2019 - 22h
  
✓ You're going to restore this backup: 23/11/2019 - 22h

➤ Do you want to perform a backup before restoring? (y/n): y

➤ Please confirm by typing the broker instance name: my-kafka

✓ Backup successfuly created
✓ Backup as successfuly been restored (23/11/2019 - 22h)
```

