---
description: Configure your notifications paths
---

# Notifications

Notification is useful when Qovery wants to notify you about important things happening on your accounts. As well it is useful to you to receive notification on topics or alerts you want to get.

Qovery offers several ways to be notified. It's up to you to chose one or multiple solution.

## Slack

[Slack](https://slack.com/) is a well known collaboration hub teams to work together seamlessly. To be notified, look at the Qovery app on the Slack Directory, then click on the "Add to Slack" button.

Once done, your Slack account is linked to your project. In order to receive notification for this specific project, you can add this:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  notification:
    - type: slack
      channel: qovery-notifications
```
{% endtab %}
{% endtabs %}

Qovery notifications will be sent to `#qovery-notifications` Slack channel.

## Email

You can receive email notifications simply by configuring the receiver email in the Qovery configuration file:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: myapp
  project: test
  notification:
    - type: email
      destination: qovery-notifs@mycompany.com
```
{% endtab %}
{% endtabs %}

