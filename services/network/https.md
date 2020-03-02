---
description: Add security to your website
---

# https \(SSL/TLS\)

The SSL/TLS certificates are mandatory to get a **secure** website.

## Get a certificate

{% hint style="success" %}
You don't have to perform any actions to get https
{% endhint %}

Y**ou simply have to set the "publicly\_accessible" parameter** in the .qovery.yml file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  publicly_accessible: true
```
{% endtab %}
{% endtabs %}

Then commit and push to apply this new change.

Then, to get the status of your application from the CLI to get the https URL:

```bash
$ qovery status

BRANCHES NAME	STATUS        	ENDPOINTS                       APPLICATIONS	DATABASES	BROKERS	STORAGE 
master       	up and running	https://xxx-main-gtw.qovery.io	1           	1        	0      	0      	

APPLICATIONS NAME	STATUS        	ENDPOINTS                    	DATABASES	BROKERS	STORAGE 
simple-example   	up and running	https://yyy-xxx-app.qovery.io	1        	0      	0      	
```

You can also see it from the Web interface.

