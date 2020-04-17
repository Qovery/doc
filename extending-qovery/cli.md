---
description: Qovery Command Line Interface (CLI)
---

# CLI

## Installation

### Mac OS

#### Homebrew

The common solution to install a command line binary on Mac OS is to use [brew](https://brew.sh/):

```text
brew tap Qovery/qovery-cli
brew install qovery-cli
```

#### Manual

This is the solution to install Qovery manually:

```text
curl -s https://get.qovery.com | bash
```

### Windows

#### Scoop

The classic way to install binaries on Windows is to use [Scoop](https://scoop.sh/):

```text
scoop bucket add qovery https://github.com/Qovery/scoop-qovery-cli
scoop install qovery-cli
```

#### Manual

You can [download the latest releas](https://github.com/Qovery/qovery-cli/releases)e and uncompress its content to any arbitrary folder of your choosing on your local workstation (e.g. c:\qovery, c:\myapps). We suggest you also add that folder to your PATH enviroment to simplify the way your run the qovery CLI.

### Linux

You can download and install Qovery CLI from on every Linux distribution:

```text
curl -s https://get.qovery.com | sudo bash
```

## Upgrade

To upgrade with your package manager, please report to it to know the upgrade recommendations.

To manually upgrade the binary, use the built in function:

```bash
sudo qovery upgrade
```





