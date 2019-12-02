---
description: Qovery configuration initialization
---

# Initialization

In order to get a quick Qovery configuration file, you can use the CLI to generate one:

```text
$ qovery init

✓ Dockerfile detected in your root directory

➤ Enter the project name: my-project

➤ What port number your application ir running on? (Hit enter if none): 8080

➤ Is this port accessible from other applications of the same project? (y/n): y

➤ Would you like to expose publicly your application on https? (y/n): y

➤ Do you need any database? (y/n): n

➤ Do you need any broker? (y/n): n

✓ Your Qovery configuration file has been successfuly created (.qovery.yml)!
✓ Commit into your repository and push it to get this deployed.
```

In your current directory, you now have a **".qovery.yml" file describing the desired configuration** you've just asked for.

If you want more services or get a fined grained configuration, you can take a look at the [Services section](../services/network/).



