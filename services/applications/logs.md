---
description: View your application logs
---

# Logs

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

