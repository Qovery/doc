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
➤ Pick up those you need (comma separated): 3,4,6
1. PostgreSQL
2. MongoDB
3. MySQL
4. Redis
5. Memcached
6. Elasticsearch
➤ Do you need any borker? (y/n): n

✓ Your Qovery configuration file has been successfuly created (.qovery.yml)!

➤ Commit into your repository and push it to get this deployed.
```

In your current directory, you now have a ".qovery.yml" file describing the desired configuration you've just asked for.

If you want more services, you can take a look at the [Services section](../services-1/network/).



