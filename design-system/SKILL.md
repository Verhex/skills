---
name: design-system
description: Define or change a shared UI component, variant, design token or component rule in any product (web, mobile, desktop, terminal, voice or embedded) - reusable system decisions rather than a one-off screen.
---

# Design system

Turn patterns the product has already proven into a governed, reusable system. This skill fixes the order of
work and what a shared piece must specify. It prescribes no framework, component library, token format or
platform: use the ones the project already has.

## 1. Read the project first

Find what exists before proposing anything: the platforms the product ships on, the UI toolkit, the current
components, where style values live, how text is translated and which accessibility rules the team follows.
Name the platforms in scope for this change. A platform the product does not ship on is out of scope; a
platform it plans to ship on is a named dependency, not a finished target.

Done when the platforms in scope, the existing components touched and the current source of style values are
written down.

## 2. Workflow, then pattern, then component, then token

Start from a real user workflow, never from an abstract component inventory.

1. Pick the workflow and its states: success, failure, empty, loading, permission-limited, offline.
2. Find what repeats across two or more real screens. One occurrence is a screen detail, not a pattern.
3. Write the component contract (step 3) for what repeats.
4. Derive tokens last (step 4), from the values the contracts actually share.

Done when every proposed component names the real screens that use it.

## 3. Component contract

A shared component specifies each of these, or says "not applicable" with the reason:

1. Purpose and the source of the data it shows.
2. Anatomy and content order.
3. Variants, and when each is used.
4. States: default, focused, active, selected, disabled, loading, empty, stale, partial, error and recovery.
5. Input: every way the platform offers (touch, pointer, keyboard, remote, voice, switch). Each action is
   reachable by more than one where the platform has more than one.
6. Focus or selection order, and where focus goes after the component closes or changes.
7. Accessible name, role and description in the platform's own accessibility model.
8. How changes are announced to assistive technology when content updates on its own.
9. Text: translation, expansion in longer languages, right-to-left where the product supports it,
   user-chosen text size.
10. Platform adaptations: what differs per platform in scope and what stays the same.
11. Token dependencies.
12. Behaviour with large data, slow networks and low-power devices.
13. Proof required: tests of behaviour and real rendered captures of the adverse states.

A component with only its happy state is not complete.

## 4. Tokens

Use three layers, in whatever format the project's tooling supports:

- **Primitive**: raw values (a colour, a size, a duration). Components never read these directly.
- **Semantic**: product meaning independent of any component (surface, text, danger, focus, spacing step).
- **Component**: only for a stable, component-specific need that no semantic token covers.

Reuse a fitting token before adding one. State meaning stays the same across themes, densities and platforms.
A user's theme, contrast, text-size and motion preferences are data to honour and migrate, never to discard.
One source generates every platform's values; a hand-edited generated file is a defect.

Done when no component in the change reads a raw value and every new token names what it means.

## 5. Same meaning, native form

Share meaning and structure across platforms, not pixels. Each platform keeps its own conventions for
navigation, gestures, system controls, typography scale and density. A platform may drop an interaction only
when its limit is stated and another way to do the same thing exists.

## 6. Governance

- Each public component and token has an owner and a stated effect when it changes.
- Extend an existing component before copying it.
- Remove with a migration path, evidence of current use and a removal date.
- Local one-off variants and raw-value escapes are findings, listed and decided, not silently kept.
- Examples use realistic content: long strings, large numbers, missing data, error states.
- Check against the current accessibility standard for each platform in scope (for example WCAG and the
  platform vendor's guidelines); verify the current version before citing it.

## 7. Check

Pick checks that match the changed contract: behaviour and adverse paths, accessibility on a real device or
assistive technology, token generation consistency, and rendered states on each platform in scope. Skip tests
that only mirror low-impact styling. A gallery or static specimen shows the design, not that the product uses
it.

Done when each platform in scope has real rendered evidence for the changed states, and anything unverified
is listed as unverified.
