---
title: "Toggle alert"
action: alert.toggle
domain: alert
description: "Acknowledges an alert, or resets it if it was already acknowledged."
related_actions:
  - alert.turn_on
  - alert.turn_off
---

Use this action to flip an alert between acknowledged and reset. If the alert is acknowledged, it is reset and can notify you again. If it isn't acknowledged, it is acknowledged and its notifications stop.

An [alert](/integrations/alert/) reminds you about something that needs attention, such as a garage door left open or a low battery.

{% include actions/ui_header.md %}

To toggle an alert from an automation or a script:

1. Go to {% my automations title="**Settings** > **Automations & scenes**" %}.
2. Open an existing automation or script, or select **Create automation** > **Create new automation**.
3. If you're setting up a new automation, add a trigger in the **When** section. Scripts don't need a trigger. They run when something else calls them.
4. In the **Then do** section, select **Add action**.
5. Select what you want to control. Under **By target** (see [Targets](#targets)), select the alert you want to toggle.
6. From the actions shown for that target, select **Toggle**.
7. Select **Save**.

### Options in the UI

This action has no additional options beyond the target.

{% include actions/yaml_header.md %}

In YAML, refer to this action as `alert.toggle`. A basic example looks like this:

{% example %}
action: |
  action: alert.toggle
  target:
    entity_id: alert.garage_door
{% endexample %}

This acknowledges `alert.garage_door` if it wasn't acknowledged yet, and resets it if it was.

### Options in YAML

This action has no additional YAML options beyond the target.

{% include actions/targets.md %}

## Good to know

- If the alert is set up with `can_acknowledge` turned off, acknowledging fails with an error saying the alert cannot be acknowledged.
- If you need a specific result, use [Turn on alert](/actions/alert.turn_on/) or [Turn off alert](/actions/alert.turn_off/) instead.

{% include actions/try_it.md %}

{% include actions/stuck.md %}

{% include actions/related.md %}
