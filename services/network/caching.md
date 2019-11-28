---
description: Speed up your web application access
---

# Caching \(CDN\)

A content content distribution network \(CDN\) is a geographically distributed network of proxy servers to **provide high availability and high performance** by **distributing the service spatially** relative to end-users.

A common use case is to accelerate images, CSS or JavaScript browser loading.

## Qovery caching

Activating the standard cache on Qovery is the **easiest way to speed up your website**.

Here are the advantages of enabling this feature:

* Support **SSL/TLS 1.3**
* **Automatic** [**minify**](https://en.wikipedia.org/wiki/Minification_%28programming%29) of CSS, JavaScript and HTML pages
* \*\*\*\*[**Brotli** **compression**](https://en.wikipedia.org/wiki/Brotli)\*\*\*\*
* Force **browser caching** expiration to **4h**
* \*\*\*\*[**Http/2**](https://en.wikipedia.org/wiki/HTTP/2) support
* \*\*\*\*[**Http/3**](https://en.wikipedia.org/wiki/HTTP/3) **with** [**QUIC**](https://en.wikipedia.org/wiki/QUIC) support
* **IP Geolocation** with "CF-IPCountry” header to all requests

The limitation are:

* you can't disable or customise one of the feature listed above
* the **maximum upload size** per request limited to **100Mb**

To enable Qovery caching, you simply have to add the "cache" line like:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  cache: qovery
  private-port: 8080
  public-port: 443
```
{% endtab %}
{% endtabs %}

