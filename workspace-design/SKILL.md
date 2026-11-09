---
name: workspace-design
description: Design an app's shell and navigation structure - screens, tabs, panels, sheets, split views, sidebars, command or search entry, focus and state restoration, saved layouts - for any form factor: phone, tablet, desktop, web, terminal, TV or watch.
---

# Workspace design

Design the frame the product's work happens in: how a person moves between places, keeps their context and
gets back to where they were. This skill prescribes no shell style. A phone app with a tab bar, a desktop app
with docked panes and a terminal app with one scrolling surface are all valid answers; the product's users,
devices and work decide.

## 1. Read the product and its platforms

Before proposing a structure, establish:

- the platforms and form factors the product ships on, and the UI toolkit of each;
- the main workflow and the two or three things a person does most;
- how long a session lasts and whether work continues in the background;
- which inputs each device offers: touch, pointer, keyboard, remote, voice, assistive technology;
- what the product already has, and which parts people rely on.

A structure that needs a capability the platform does not have is invalid until that capability is named as
a dependency.

Done when the form factors in scope and the main workflow are written down.

## 2. Shell model

Define each of these for the product; say "not applicable" where a form factor has none:

- **Global navigation**: how a person reaches the top-level places, and how many there are.
- **Scope**: which account, project or item the person is in, and how they switch.
- **Primary work area**: where the main task happens and what stays visible during it.
- **Secondary detail**: where detail, properties or evidence appear (a pushed screen, a sheet, a side panel,
  a split view, an inline expansion).
- **Transient versus durable**: what is a short-lived overlay and what is a place the person can return to.
- **Command and search entry**: how a person reaches an action or item without navigating to it.
- **Background work**: how running or finished work stays discoverable after the person moves away.

Use the platform's own navigation patterns unless the product's work gives a concrete reason to depart from
them; when departing, name the reason and the cost. Copy a proven app that does the same job and name the
behaviour copied.

Done when the main workflow can be walked start to finish through the model on every form factor in scope.

## 3. Adapt across sizes instead of shrinking

One structure, expressed per size class. Decide for each form factor what collapses, what stacks and what
moves: a side panel on a wide window may become a pushed screen on a phone; a tab bar may become a sidebar on
a tablet. Equivalent capability and meaning matter; identical layout does not.

Resolve from the start, for the form factors in scope:

- small through large screens, rotation, split-screen and resizable windows;
- multiple windows or monitors and differing scale factors, where the platform has them;
- safe areas, notches, system bars and on-screen keyboards;
- user text size, zoom, display scaling, reduced motion and high-contrast settings;
- platform conventions that differ (back behaviour, modifier keys, system gestures);
- very long labels, translated text and right-to-left layout where supported;
- large lists, trees and histories without blocking interaction.

## 4. Interaction rules

- Every action is reachable by each input the platform offers, never by one gesture or hover alone.
- Focus or reading order follows the work, not the accident of layout.
- Closing, dismissing or going back returns to a predictable place with focus restored.
- Resizable regions have minimum sizes, a non-drag way to resize and announced values.
- Tabs and items show unsaved, live, stale, failed and needs-attention states without relying on colour.
- Command and search results show what they act on and what will happen.
- Resetting the layout is clearly different from deleting the person's data.
- After reconnecting or relaunching, the shell shows the true current state, not a stale snapshot.

## 5. State restoration and saved layouts

Decide what survives leaving and returning: the place, scroll position, open panels, unsent input, selection.
The platform may end the app at any time; restoration is part of the design, not an extra.

Where the product lets people arrange their own layout, treat the layout as their data: versioned, migrated
when the app changes, recovered safely when a saved part no longer exists, and scoped to the right account or
project. Never silently discard it.

## 6. Check

Provide a map of places and transitions, the input routes for the main workflow, the focus and back cases,
captures at each size class in scope, and restoration tested by actually ending and relaunching the app.
Proof comes from the real app on a real device or window; a mock-up shows hierarchy only.

Done when the main workflow, the adverse paths and restoration have real evidence on every form factor in
scope, and untested ones are listed as untested.
