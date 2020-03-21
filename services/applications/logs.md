---
description: View your application logs and debug
---

# Logs and debug

Understanding what's going on with your application or with the deployment is one of the mandatory things a developer wants to know

First of all,you can take a look at the [status](./#status) to look at a reported problem by Qovery.

## Logs

Once an application is deployed, you can look at the logs with the help of the CLI:

```bash
$ qovery log
Can't connect to Twitter API, please add a Token
Exit
```

 If you have a running application with several logs you would like to **follow in real time**, you can do it with `-f` argument:

```bash
$ qovery log -f
```

In the case you just want to **display the last 100 lines** of the logs:

```bash
$ qovery log --tail 100
```

You can also combine them:

```bash
$ qovery log --tail 100 -f
```

It will display the last 100 log lines and continue to show in real time the logs.

## Run your application locally

You can run your application locally with Qovery magic sauce this way:

```bash
$ qovery run
```

This will build your application and run it locally. You will get access to your resources to validate the correct start of your application.

