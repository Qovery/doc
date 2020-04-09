---
description: >-
  Quickstart to deploy a Hasura application with Qovery - Estimated time: < 6
  min
---

# Deploy a Hasura application with PostgreSQL

### Step 1: Installing Qovery CLI \(estimated time: 15 sec\)

Instructions are available [here](../../extending-qovery/cli.md)

### Step 2: Sign up \(estimated time: 10 sec\)

Instructions are available [here](../sign-up.md)

### Step 3: Deploying \(estimated time: 5 min\)

You can deploy Hasura GraphQL Engine with Postgres by running followings shell scripts at the root of your project directory:

1/ Bootstrap Hasura configuration using Qovery CLI

```bash
qovery template hasura
```

2/ Point Hasura to your Postgres database and enable Hasura Console using environment variables

```bash
qovery application env add HASURA_GRAPHQL_DATABASE_URL '$QOVERY_DATABASE_MY_POSTGRESQL_DATABASE_CONNECTION_URI'
qovery application env add HASURA_GRAPHQL_ENABLE_CONSOLE true
```

3/ Commit and push your changes

```bash
git add .
git commit -m "Deploy Hasura on Qovery"
git push -u origin master
```

After pushing your changes, database and Hasura deployment will start. You can use `qovery status --watch` to track the progress. Once the deployment is done, you'll see your Hasura application URL in the status:

```bash
  ➜ qovery status
  BRANCH NAME | STATUS  | ENDPOINTS                                   | APPLICATIONS | DATABASES
  master      | running | https://yourhasura-xyz.qovery.io | demo      | none

  APPLICATION NAME | STATUS  | ENDPOINT                                       | DATABASES
  demo          | running | https://yourhasura-xyz.qovery.io | none
```

### Do you need any help?

[Join us on Discord](https://discord.qovery.com)

