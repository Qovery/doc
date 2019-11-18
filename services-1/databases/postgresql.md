---
description: 'PostgreSQL is a high-performance, standards-compliant relational SQL database.'
---

# PostgreSQL

[PostgreSQL](https://www.postgresql.org/) is a powerful, open source **object-relational database system** with over 30 years of active development that has earned it a strong reputation for **reliability, feature robustness, and performance**.

## Creating an instance

To create a new dedicated PostgreSQL instance, you can use Qovery CLI to do it:

```bash
$ qovery add database

➤ Choose the database instance you want to add: 1
1. PostgreSQL
2. MongoDB
...

➤ Set the instance name: my-super-instance

➤ Estimated PostgreSQL data size in GiB (default: 10): 20

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

## Get instance status

To know more about your instance status, you can do it this way:

```bash
$ qovery status database

✓ my-super-instance:
* Type  : PostgreSQL
* Size  : 20GiB
* Kind  : Medium (4 vCPU / 16GiB Ram)
* Backup: Daily / Kept 30 days
```







