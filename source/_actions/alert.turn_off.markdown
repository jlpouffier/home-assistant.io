---
title: "Turn off alert"
action: alert.turn_off
domain: alert
description: "Acknowledges an alert, so it stops sending notifications."
related_actions:
  - alert.turn_on
  - alert.toggle
---

Use this action to acknowledge an alert. Acknowledging tells Home Assistant that you have seen it, so the repeating notifications stop until the alert resets.

An [alert](/integrations/alert/) reminds you about something that needs attention, such as a garage door left open or a low battery. This action is a good fit for a button in a notification that lets you dismiss the reminder.

{% include actions/ui_header.md %}

To acknowledge an alert from an automation or a script:

1. Go to {% my automations title="**Settings** > **Automations & scenes**" %}.
2. Open an existing automation or script, or select **Create automation** > **Create new automation**.
3. If you're setting up a new automation, add a trigger in the **When** section. Scripts don't need a trigger. They run when something else calls them.
4. In the **Then do** section, select **Add action**.
5. Select what you want to control. Under **By target** (see [Targets](#targets)), select the alert you want to acknowledge.
6. From the actions shown for that target, select **Turn off**.
7. Select **Save**.

### Options in the UI

This action has no additional options beyond the target.

{% include actions/yaml_header.md %}

In YAML, refer to this action as `alert.turn_off`. A basic example looks like this:

{% example %}
action: |
  action: alert.turn_off
  target:
    entity_id: alert.garage_door
{% endexample %}

This acknowledges the `alert.garage_door` alert and stops its notifications.

### Options in YAML

This action has no additional YAML options beyond the target.

{% include actions/targets.md %}

## Good to know

- The alert must allow acknowledgment. If the alert is set up with `can_acknowledge` turned off, the action fails with an error saying the alert cannot be acknowledged.
- You still receive the done message when the condition the alert watches becomes false again.
- To let the notifications start again, use [Turn on alert](/actions/alert.turn_on/).

{% include actions/try_it.md %}

{% include actions/more_examples.md %}

### Automation: acknowledge the garage door alert from a chat button

Stop the repeating reminder when you confirm you have seen it.

- **Trigger**: A callback arrives from your chat app
- **Action**: Turn off
  - **Target**: Garage door alert

{% details "Show example YAML" %}

{% example %}
automation: |
  - alias: "Telegram callback to stop alerts for garage door"
    triggers:
      - trigger: event
        event_type: telegram_callback
        event_data:
          data: "/garage_acknowledge"
    actions:
      - action: alert.turn_off
        target:
          entity_id: alert.garage_door
{% endexample %}

{% enddetails %}

{% include actions/stuck.md %}

{% include actions/related.md %}
