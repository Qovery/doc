---
description: Qovery Sigh Up
---

# Sign Up

**Qovery Sign Up is the first step before using it.**

To do so, you have 2 options, select the one you're more familiar with:

1. \*\*\*\*[**Web interface**](sign-up.md#web-interface): if you prefer visual interfaces, more graphical, use our dedicated web interface.
2. \*\*\*\*[**CLI**](sign-up.md#cli): if you prefer the command line, you can safely use our CLI. It contains a wizard to help you to quickly generate a configuration.

Both will help you to authenticate and do more afterwards.

## Web interface

1. To sign up using Qovery Web Interface, you just have to go on [cloud.qovery.com](https://cloud.qovery.com).
2. You have the choice to sign up by using [Github](https://github.com/), [Gitlab](https://about.gitlab.com) and [Bitbucket](https://bitbucket.org/).

![](../.gitbook/assets/q-register.png)

## CLI

### Installation

#### Mac OS

There are 2 ways to install the Qovery CLI on Mac OS. First the common one with [brew](https://brew.sh/):

```text
brew install qovery
```

The second option is with this command line:

```text
curl -LO https://cli.qovery.com/darwin/qovery
```

#### Windows

Qovery CLI can be installed on Windows from this [link](https://cli.qovery.com/windows/qovery).

Then add it in one folder of your PATH \(eg. C:\Windows\)

#### Linux

You can download and install Qovery CLI:

```text
curl -LO https://cli.qovery.com/linux-x64/qovery
chmod 755 qovery
sudo mv qovery-cli /usr/local/bin/qovery
```

You may also find "qovery" CLI to install from your package manager. Please refer to it to know more.

### Sign Up

To sign up using Qovery CLI, it's simple. Run this command:

```text
qovery connect
```

You'll get a window open on your browser to link with your GitHub account.

### Help

To list all available commands

```text
qovery help
```

CLI [source code](https://github.com/Qovery/qovery-cli) is available on GitHub

