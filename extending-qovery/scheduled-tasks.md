---
description: Run scheduled jobs when you want
---

# Scheduled jobs

Scheduled tasks are useful to create **periodic and recurring jobs**. Here are some useful use cases:

* **Cleaning data content**: your application has to throw out unused data or temporary data. Every hour a cleaning job contact your application to request cleaning
* **Run backups**: perform regular backups of some type of your data \(eg: after manipulation\) every day
* **Send mails**: being able to send emailings every week

You can declare 2 kinds of scheduled jobs:

1. **http requests**: simply run http requests against your apps for example
2. **Scripts**: add scripts to your application container and they will be executed

To specify the **date and time** of scheduled jobs, we're using the well known [**Cron** system](https://en.wikipedia.org/wiki/Cron).

## http requests

Here is the simplest solution, you can perform several http requests. Add the "scheduled-tasks" in your Qovery configuration file with a list of all the tasks you want to execute.

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
...
scheduled-tasks:
  - name: clean-old-data
    url: http://myapp/api/v1/jobs/clean-old-data
    cron: 0 0 * * *
```
{% endtab %}
{% endtabs %}

Here, the url with be called every day at midnight and will target.

## Scripts

Scripts are the most flexible way to do what you want to do. You simply have to create scripts, dedicated applications or whatever you want inside your application container. Then you'll be able to call it.

{% hint style="danger" %}
**Your Dockerfile shouldn't have ENTRYPOINT, but CMD parameter to run your application. Otherwize your application will be launched once the scheduled job will start.**
{% endhint %}

Add the "scheduled-tasks" in your Qovery configuration file with a list of all the tasks you want to execute:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
...
scheduled-tasks:
  - name: clean old data
    command: /opt/schedule/clean-old-data.sh
    cron: 0 0 * * *
  - name: delete all tmp files
    command: python /opt/schedule/del-tmp-files.py
    cron: 0 */2 * * *
```
{% endtab %}
{% endtabs %}

There are 2 jobs here running at different interval time

## Jobs history status

You can get the jobs history status easily through the CLI or the Web interface.

{% hint style="info" %}
Qovery keeps the history of the last 10 jobs 
{% endhint %}

To access this information, you can use the CLI:

```bash
$ qovery job status

History of the last job status:
1. clean old data - 00:00:00 01/01/2020 : ok
2. delete all tmp files - 00:00:00 01/01/2020: ok
3. delete all tmp files - 22:00:00 31/12/2019: ok
4. delete all tmp files - 20:00:00 31/12/2019: ok
5. delete all tmp files - 18:00:00 31/12/2019: ok
...
```

{% hint style="success" %}
If you configured the [notifications](monitoring/notifications.md), **you'll receive alerts when a job fail**
{% endhint %}

## Jobs logs

You can get the jobs logs status easily through the CLI or the Web interface.

For the CLI, from the `qovery job status` command, just get the number 

```bash
$ qovery job log 1

2019-11-21 13:31:59.423  INFO [core,3938bfb6adaa8a38,3938bfb6adaa8a38,true]
2019-11-21 13:41:59.424  INFO [core,323e8fcef1d6c99b,323e8fcef1d6c99b,true]
...
```



