---
description: Let's start with a simple application
---

# Simple application

## Description

In this example, we're taking a **single simple application**. You'll **see how fast it is** to deploy it.

We'll start new project with those constraints:

| Prerequisites | Comments |
| :--- | :--- |
| 1 application | Private port on 8080 |
| Being exposed through internet on https | Public port on 443 |

## Generate configuration

The first thing to do is to initiate Qovery in the repository:

```text
$ qovery init
Reply to the following questions to initialize Qovery for this application
For more info: https://docs.qovery.com

➤ What do you want?:
1. create a new project
2. select an existing project
➤ Your choice: 1

➤ Enter the project name: project-demo

➤ Choose the region where you want to host your project and applications:
0. none
1. aws/eu-west-3
➤ Your choice: 1

➤ Enter the application name [default: simple-example]: demo

➤ Do you need a database? (PostgreSQL, MySQL, MongoDB, ...) (y/n) [default=n]: n
✓ Your Qovery configuration file has been successfully created (.qovery.yml)

!!!IMPORTANT!!!
Qovery needs to get access to your git repository
https://github.com/apps/qovery/installations/new

➤ Would you like to open the link above? (y/n) [default=n]: y

!!!IMPORTANT!!!
1/ Commit and push the ".qovery.yml" file to get your app deployed
➤ Run: git add .qovery.yml && git commit -m "add .qovery.yml" && git push -u origin master

2/ Check the status of your deployment
➤ Run: qovery status

Enjoy! 👋
```

{% hint style="info" %}
If you do not already have a Dockerfile in your repository, one will be suggested according to your repository content.
{% endhint %}

Now that you have declared your prerequisites, you can find the result in your Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: simple-example
  project: my-project
  publicly_accessible: true
routers:
- name: main
  routes:
  - application_name: simple-example
    paths:
    - /*
```
{% endtab %}
{% endtabs %}

Then you have to add in your code the [Qovery SDK](../sdks.md) to easily manage the credentials part.

## Deploy

Finally, **once committed and pushed, your application will be live!!!** You can check the status and retrieve the URL like this:

```bash
$ qovery status

BRANCHES NAME	STATUS        	ENDPOINTS                       APPLICATIONS	DATABASES	BROKERS	STORAGE 
master       	up and running	https://xxx-main-gtw.qovery.io	1           	1        	0      	0      	

APPLICATIONS NAME	STATUS        	ENDPOINTS                     DATABASES	BROKERS	STORAGE 
simple-example   	up and running	https://yyy-xxx-app.qovery.io	1        	0      	0      	

DATABASES NAME	STATUS        	TYPES	VERSIONS	ENDPOINTS                     PORTS	USERNAME 	PASSWORDS       	APPLICATIONS   
my-mysql      	up and running	MYSQL	8.0     	xxx-yyy-zzz.aaa.amazonaws.com	3306 	username	password	        simple-example	

```

