---
description: Your data are safe and can be easily restored
---

# Backups and Restore

Backups and restore are regularly a pain point to setup. Qovery helps you to get this part **always automatically managed by the Cloud provider**.

## Backups

### Applications

When containers' applications are successfully built, **all containers are kept for future possible rollback**.

### Services

Please take a look at the desired service to know how they are backup.

## Restore

### Applications

As the Qovery configuration file is in your git repository and versioned, you can rollback any version when you want.

{% hint style="warning" %}
**When you rollback a commit containing a Qovery configuration change, ensure there's no other changes to avoid rollback unwanted modifications.**
{% endhint %}

### Services

Please take a look at the desired service to know how you can restore it.

