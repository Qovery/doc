---
description: Automate your tests before deploying
---

# CI / Tests

[Continuous Integration \(CI\)](https://en.wikipedia.org/wiki/Continuous_integration) is the practice of merging all developers working copies to a shared mainline several times a day. The main aim of CI is to prevent integration problems.

## Add tests

To add tests, you have to add to the Qovery configuration file this minimum content:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
ci:
  commands:
  - gradle task1 test
```
{% endtab %}
{% endtabs %}

You can set as many commands as you need.





