---
description: 'MongoDB is a cross-platform, document-oriented database.'
---

# MongoDB \(coming soon\)

[MongoDB](https://www.mongodb.com/) is a cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schema.

## Add a new database instance to an existing application

To **add a new dedicated MongoDB instance** to an existing application, you can use update the configuration file by adding these lines:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
...
databases:
- type: documentdb
  version: "3.6"
  name: my-mongo
```
{% endtab %}
{% endtabs %}

* **name**: the name of your MongoDB database
* **version**: the versions of MongoDB
* **type**: the database engine

## Get access to an instance

To get the connection information of your database, you can use the CLI:

```bash
$ qovery application env list -c
  SCOPE       | KEY                                                              | VALUE     
--------------+------------------------------------------------------------------+-----------
  BUILT_IN    | QOVERY_BRANCH_NAME                                               | master    
  BUILT_IN    | QOVERY_IS_PRODUCTION                                             | true      
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_NAME                               | my-mongo  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_TYPE                               | DOCUMENTDB     
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_VERSION                            | 3.6       
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_CONNECTION_URI                     | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_CONNECTION_URI_WITHOUT_CREDENTIALS | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_HOST                               | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_FQDN                               | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_PORT                               | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_USERNAME                           | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_PASSWORD                           | <hidden>  
  BUILT_IN    | QOVERY_DATABASE_MY_DOCUMENTDB_DATABASE                           | DOCUMENTDB 
```

## Get instance status

To know more about your instance status, you can do it this way:

```bash
$ qovery status -c
...
  DATABASE NAME | STATUS  | TYPE       | VERSION | ENDPOINT | PORT     | USERNAME | PASSWORD | APPLICATIONS    
----------------+---------+------------+---------+----------+----------+----------+----------+-----------------
  my-mongo      | running | DOCUMENTDB | 3.6     | <hidden> | <hidden> | <hidden> | <hidden> | simple-example  
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
  - name: my-mongo
    type: documentdb
    backup-window: 21-23
```
{% endtab %}
{% endtabs %}

As described here, the backup will occur between 9PM and 11PM.

