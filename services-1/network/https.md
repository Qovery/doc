# Https \(SSL/TLS\)

The SSL/TLS certificates are mandatory to get a website accessible through https.

In order to get a SSL/TLS certificate, **you simply have to set the "public-port" parameter to "443"** in the .qovery.yml file:

```yaml
app:
  name: myapp
  public-port: 443
  project: test
```

Get the status of your application from the CLI to get the https URL:

```bash
$ qovery status

* External DNS name               : <myapplicationid>.qovery.io
* SSL/TLS enabled                 : https://<myapplicationid>.qovery.io
* Current deployed version        : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```



