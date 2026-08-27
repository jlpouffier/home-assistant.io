---
title: "Turn on alert"
action: alert.turn_on
domain: alert
description: "Resets an alert, so it sends its notifications again."
related_actions:
  - alert.turn_off
  - alert.toggle
---

Use this action to reset an alert that you acknowledged earlier. The alert starts sending its repeating notifications again as long as the condition it watches is still true.

An [alert](/integrations/alert/) reminds you about something that needs attention, such as a garage door left open or a low battery. Acknowledging it silences the notifications. This action undoes that.

{% include actions/ui_header.md %}

To reset an alert from an automation or a script:

1. Go to {% my automations title="**Settings** > **Automations & scenes**" %}.
2. Open an existing automation or script, or select **Create automation** > **Create new automation**.
3. If you're setting up a new automation, add a trigger in the **When** section. Scripts don't need a trigger. They run when something else calls them.
4. In the **Then do** section, select **Add action**.
5. Select what you want to control. Under **By target** (see [Targets](#targets)), select the alert you want to reset.
6. From the actions shown for that target, select **Turn on**.
7. Select **Save**.

### Options in the UI

This action has no additional options beyond the target.

{% include actions/yaml_header.md %}

In YAML, refer to this action as `alert.turn_on`. A basic example looks like this:

{% example %}
action: |
  action: alert.turn_on
  target:
    entity_id: alert.garage_door
{% endexample %}

This resets the `alert.garage_door` alert.

### Options in YAML

This action has no additional YAML options beyond the target.

{% include actions/targets.md %}

## Good to know

- Resetting an alert doesn't start notifications on its own. They only resume if the condition the alert watches is still true.
- An alert has three states: `idle` when its condition is false, `on` when the condition is true, and `off` when the condition is true but you acknowledged the alert.
- To silence an alert instead, use [Turn off alert](/actions/alert.turn_off/).

{% include actions/try_it.md %}

{% include actions/stuck.md %}

{% include actions/related.md %}
