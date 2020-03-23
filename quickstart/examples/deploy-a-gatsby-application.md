---
description: >-
  Quickstart to deploy a Gatsby application with Qovery - Estimated time: < 2
  min 20
---

# Deploy a Gatsby application

### Step 1: Installing Qovery CLI \(estimated time: 15 sec\)

Instructions are available [here](../../extending-qovery/cli.md)

### Step 2: Sign up \(estimated time: 10 sec\)

Instructions are available [here](../sign-up.md)

### Step 3: Deploying \(estimated time: 2 min\)

You can deploy your Gatsby application by running the following command in the root of the project directory:

```bash
# Generate the .qovery.yml file
$ qovery init
```

Add this Dockerfile at the root of your project directory

{% code title="Dockerfile" %}
```bash
FROM node:12-buster as build

RUN yarn global add gatsby-cli
WORKDIR /app
ADD . ./
RUN yarn
RUN gatsby build

FROM gatsbyjs/gatsby
COPY --from=build /app/public /pub

EXPOSE 80
```
{% endcode %}

Commit, push and your React application is deployed

```bash
# Git commit and push your code
$ git add .qovery.yml
$ git commit -m "add .qovery.yml file"
$ git push -u origin master

# App deployed!
```

Get your application URL

```bash
$ qovery status

  BRANCH NAME  | STATUS  | ENDPOINTS                      | APPLICATIONS | DATABASES | BROKERS | STORAGE
  master       | running | https://xxx-main-gtw.qovery.io | 1            | 0         | 0       | 0

  APPLICATION NAME | STATUS  | ENDPOINT                      | DATABASES | BROKERS | STORAGE
  react            | running | https://xxx-yyy-app.qovery.io | 0         | 0       | 0
```

### Do you need any help?

[Join us on Discord](https://discord.qovery.com)

