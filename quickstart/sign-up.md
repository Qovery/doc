---
description: Qovery Sign Up
---

# Sign Up

**Qovery Sign Up is the first step before using it.**

To do so, you have 2 options, select the one you're more familiar with:

1. \*\*\*\*[**Web interface**](sign-up.md#web-interface): if you prefer visual interfaces, more graphical, use our dedicated web interface.
2. \*\*\*\*[**CLI**](sign-up.md#cli): if you prefer the command line, you can safely use our CLI. It contains a wizard to help you to quickly generate a configuration.

Both will help you to authenticate and do more afterwards.

## Web interface

1. To sign up using Qovery Web Interface, you just have to go on cloud.qovery.com.
2. You have the choice to sign up by using [Github](https://github.com/), [Gitlab](https://about.gitlab.com) and [Bitbucket](https://bitbucket.org/).

![](../.gitbook/assets/q-register.png)

## CLI

### Installation

#### Mac OS \(brew\)

The common solution to install a command line binary on Mac OS is to use [brew](https://brew.sh/):

```text
brew tap Qovery/qovery-cli
brew install qovery
```

#### Mac OS \(manual\)

This is the solution to install qovery manually:

```text
curl -s https://raw.githubusercontent.com/Qovery/qovery-cli/master/install.sh | bash
```

#### Windows \(scoop\)

The classic way to install binaries on Windows is to use [Scoop](https://scoop.sh/):

```text
scoop bucket add app https://github.com/org/repo.git
scoop install qoveryc-cli
```

#### Windows \(manual\)

You can [download the latest releas](https://github.com/Qovery/qovery-cli/releases)e and uncompress its content to _C:\Windows_.

Now in the Command line Terminal, you can type "qovery".

#### Linux

You can download and install Qovery CLI:

```text
curl -s https://raw.githubusercontent.com/Qovery/qovery-cli/master/install.sh | bash
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

