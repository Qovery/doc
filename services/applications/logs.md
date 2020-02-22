---
description: View your application logs
---

# Logs

Once you've deployed your application, you can use the `status` parameter to look at the status.

But in case of failure, your application may encounter an issue to start. Looking at the application logs is generally the first thing to do.

That's why you can **use the CLI to visualize logs**:

```bash
$ qovery log
Can't connect to Twitter API, please add a Token
Exit
```

 If you have a running application with several logs you would like to **follow in real time**, you can do it with `-f` argument:

```bash
$ qovery log -f
```

