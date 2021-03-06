---
description: Frequently Asked Questions
---

# FAQ

## What is the difference between a Project, an Application and an Environment?

A project is the site that you're working on. Each project can contain multiple applications and be deployed in their own environments.

An environment is a standalone copy of your site, complete with code, data, and running services. The master branch is the production environment, while any other branch can be setup as an otherwise identical testing environment. 

## Are databases backed-up?

Yes, Qovery databases rely on Managed Services provided by AWS \(Amazon Web Services\). All databases are fully backed-up every day and incrementally on each write.

## Is Qovery production ready?

Not yet, the product is currently in beta. We hope having a production ready version for June 2020.

## Where are located your servers?

Qovery rely on the excellent AWS \(Amazon Web Services\) infrastructure. Qovery is available in United States, Canada, South America, Europe, Africa, Asia. 

## Qovery says it's deployed but I've an error "Could not resolve host"

It's generally a DNS cache issue. Very common on Mac OS, you can flush your cache this way:

```bash
sudo dscacheutil -flushcache
sudo killall -HUP mDNSResponder
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
```

If you want to know more about it, please take a look at the [official Apple page](https://support.apple.com/en-us/HT202516). 

## My application is not able to start, I've a timeout error

This can happen if your application is too long to start. Please contact us [support@qovery.com](mailto:support@qovery.com).

## How can I contact you?

Feel free to contact us by email at [**hello@qovery.com**](mailto:hello@qovery.com)\*\*\*\*

