---
description: Shared filesystem content across your containers
---

# NFS

[Network File System \(NFS\)](https://en.wikipedia.org/wiki/Network_File_System) is a **distributed file system** protocol, allowing a user on a client computer to access files over a computer network much like local storage is accessed.

![](../../.gitbook/assets/qovery-nfs.png)

## Create a new NFS storage

To enable NFS, edit the Qovery configuration file and add this:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
...
storage:
  - name: my-shared-data
    type: nfs
```
{% endtab %}
{% endtabs %}

As you can see, there is a **declared storage called "my-shared-data"**.

## Access to an NFS storage

To allow your application to use it in the desired mount point, you have to request it in the "application" section.

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  nfs:
    - name: my-shared-data
      mount-point: /mnt/data
...
```
{% endtab %}
{% endtabs %}

Once done, the NFS share will be accessible \(here from "/mnt/data" directory\).

## Get storage status

To know more about your NFS storage status, you can do it this way:

```bash
$ qovery status storage

✓ my-shared-data:
* Branch  : master (Production)
* Health  : healthy
* Type    : NFS
```

## Delete an NFS storage

To delete a storage, there are 2 ways to do it, depending on the scenario you are.

{% hint style="danger" %}
**Delete action will drop the bucket and its data!**
{% endhint %}

{% hint style="success" %}
**Backups will be kept for 1 month if you need to recover \(just in case**😉**\)**
{% endhint %}

### Delete for all branches

If you want to **delete a NFS storage with its data.** You simply have to **delete the corresponding Qovery configuration** in your YAML file.

{% hint style="danger" %}
**Be sure you've firstly removed the mount points to all your applications \(and commited\) before removing the NFS storage.**
{% endhint %}

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  ...
storage:
  - name: my-shared-data
    type: nfs
```
{% endtab %}
{% endtabs %}

### Delete for one branch

Once you've finished to work on a feature branch, simply delete the branch and **the NFS storage will automatically be delete** as well.

