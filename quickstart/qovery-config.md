---
description: Basic Qovery configuration
---

# Qovery config

In order to get a quick Qovery configuration file, you can use the CLI to generate one:

```text
$ qovery init

✓ Dockerfile detected in your root directory
➤ Would you like to expose publicly your application? (y/n): y

➤ Do you need any database? (y/n): y

➤ Set the instance name: my-super-instance

➤ Estimated MySQL data size in GiB (default: 10): 20

➤ Please choose the performances you need: 1
1. Tiny   : 1 vCPU / 2GiB Ram
2. Small  : 2 vCPU / 8Gib Ram
3. Medium : 4 vCPU / 16GiB Ram
4. Big    : 8 vCPU / 32GiB Ram
5. Huge   : 16 vCPU / 64GiB Ram
c. Custom Mode

➤ Do you need any other database? (y/n): n

➤ Do you need any borker? (y/n): n

✓ Your Qovery configuration file has been successfuly created (.qovery.yml)!

➤ Commit into your repository and push it to get this deployed.
```

In your current directory, you now have a ".qovery.yml" file describing the desired configuration you've just asked for.

If you want more services or get a fined grained configuration, you can take a look at the [Services section](../services-1/network/).



