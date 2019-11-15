---
description: Know how you manage the network part
---

# Network

On your Qovery project, you can configure the way your applications are accessible from the [outside \(internet\)](./#public-access) or in a [private, dedicated and secure way](./#private-access) with other applications from the same project.

{% hint style="warning" %}
**By default all the network is private. Nobody can access to your applications until you explicitly specified it.**
{% endhint %}

## Closed Access

If your application do not have to expose a port, like just computing or perform any kind of tasks and store the result in S3, you may not need to expose any kind of port. So **you don't have anything to do**.

## Private Access

In the case you have several applications running in the same Qovery project, you may need to have applications talking together in a **private, dedicated and secure area**.

For example, your application called "AppB" needs to talk to another running application called "AppA". The "AppA" application has to expose its running port.

To do so, in the Dockerfile of the "AppA" application, add this line:

```bash
EXPOSE 8080
```

Here the port "8080" will be securely exposed to other applications. In order to target "AppA" application, "AppB" application has to point to "AppA:8080".

Then commit and push to apply this new change.

## Public Access

To allow public access on a specific application port, you have to first expose the port as described in the "[Private Access](./#private-access)" section of this page.

Then you have to declare in the Qovery configuration file \(.qovery.yaml\), the desired port for external access \(here 80, the http port\):

```yaml
app:
  name: myapp
  public-port: 80
  project: test
```

Then commit and push to apply this new change.

### Multiple public ports access

If you have multiple ports to publicly expose, you need to use "public-ports" instead. Here is an example:

```yaml
app:
  name: myapp
  public-ports:
    8080: 80
    8080: 443
    8081: 1234
  project: test
```

To explain it simply:

* The port exposed 8080 on the private network, is publicly exposed to the port 80 and 443
* The port exposed 8081 on the private network, is publicly exposed to the port 1234

