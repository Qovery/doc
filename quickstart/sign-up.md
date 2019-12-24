---
description: Get Qovery CLI and sign up/in
---

# Sign Up

## CLI installation

### Mac OS

#### Homebrew

The common solution to install a command line binary on Mac OS is to use [brew](https://brew.sh/):

```text
brew tap Qovery/qovery-cli
brew install qovery
```

#### Manual

This is the solution to install qovery manually:

```text
curl -s https://get.qovery.com | bash
```

### Windows

#### Scoop

The classic way to install binaries on Windows is to use [Scoop](https://scoop.sh/):

```text
scoop bucket add qovery https://github.com/Qovery/scoop-qovery-cli
scoop install qoveryc-cli
```

#### Manual

You can [download the latest releas](https://github.com/Qovery/qovery-cli/releases)e and uncompress its content to _C:\Windows_.

### Linux

You can download and install Qovery CLI from on every Linux distribution:

```text
curl -s https://get.qovery.com | bash
```

## Sign Up/In

To sign up using Qovery CLI, it's simple. Run this command:

```text
qovery auth
```

You'll get a window open on your browser to link with your account. In this example we chose GitHub :

![](../.gitbook/assets/qovery_auth.png)

We need to access to your account to be able to clone your repository for future application build:

![](../.gitbook/assets/github_connect.png)

Then we need to validate it on our side:

![](../.gitbook/assets/github_auth.png)

That's it, you should have a message saying: "_Authentication successful. You can close this window_."

