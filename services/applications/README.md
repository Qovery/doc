---
description: Easily manage your applications
---

# Applications

Applications are easy to manage on Qovery. To make it short:

* **1 project can have multiple applications**
* **1 application can only belong to 1 project**

**An application repository should contain a Dockerfile**. It should be able to build the Application and generate an image containing it \(look at the [Dockerfile page](dockerfile.md) to know more about it\).

To finish, in order to deploy to Qovery, you need to add a Qovery configuration. Here is the minimal configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
```
{% endtab %}
{% endtabs %}

Commit this file to your repository, push it and it's automatically deployed.

## Status

You can get your application status with the status command:

```text
$ qovery status
BRANCH NAME | STATUS  | ENDPOINTS             | APPLICATIONS | DATABASES | BROKERS | STORAGE  
master      | running | https://xxx.qovery.io | 1            | 0         | 0       | 0        

APPLICATION NAME | STATUS  | ENDPOINT                  | DATABASES | BROKERS | STORAGE  
myapp            | running | https://yyy-app.qovery.io | 0         | 0       | 0        

```

## Add services

You can find other proposed services by Qovery like:

| Services | Comments |
| :--- | :--- |
| [Network](../network/) | Custom DNS, SSL/TLS, Routes etc... |
| [Databases](../databases/) | SQL or NoSQL databases |
| Brokers | Message queuing systems |
| Storages | Share data against your applications |

{% hint style="info" %}
It's as easy as just adding a few lines in your configuration file!
{% endhint %}

## Delete an application with its services

You can delete an application and its associated services by deleting the environment name. First, list the deployed environments:

```bash
  $ qovery environment list
  BRANCH  | STATUS  | ENDPOINTS             | APPLICATION | DATABASES | BROKERS | STORAGE  
  master  | running | https://xxx.qovery.io | 1           | 2         | 0       | 0       
```

Ensure you're set on the correct branch \(`git checkout <branch_name>`\) and ask for suppression:

```text
$ qovery environment delete

➤ Type 'master' to delete this environment and erase its associated data: master
deletion in progress...
Hint: type "qovery status --watch" to track the progression of the deletion
```

Type the name of the branch you want to delete to validate it.

