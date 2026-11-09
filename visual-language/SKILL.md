---
name: visual-language
description: Set or revise a product's visual direction - typography, colour roles, density, spacing, hierarchy, motion, iconography and state appearance - on any platform, after the product's workflows and states are known.
---

# Visual language

Give the product a look that carries its meaning. This skill supplies a method and craft rules; it imposes no
style, palette, typeface or tone. A playful consumer app and a dense professional tool need different answers,
and the product's audience, brand and platforms decide which.

## 1. Know the product before choosing a look

Establish, from the project and the person asking:

- who uses it, in what setting, and for how long at a stretch;
- the tone the brand wants, and any existing brand material that is binding;
- the workflows and the states that must be told apart (live, stale, proposed, failed, done);
- the platforms in scope and what each controls (a terminal inherits the user's font and colours; a mobile
  app inherits system text size and dark mode; a web page inherits neither);
- visual decisions already made and accepted. Refine those; do not reopen them without a new reason.

Done when audience, tone, platforms and settled decisions are written down. Visual work on a product whose
workflow and states are still contradictory is premature; fix the model first.

## 2. Explore directions only when the identity is open

For a routine refinement, apply the settled direction and skip this step. When a durable identity or a major
visual grammar is actually being decided:

1. Hold the workflow, content and critical states constant across candidates.
2. Offer directions that differ materially. Changing only the accent colour, corner radius or background is
   one direction, not two.
3. For each, state layout grammar, type roles, density, colour behaviour, iconography, motion, accessibility
   risks and how it wears over a long session or repeated daily use.
4. Show each on the same real states: success, failure, a decision prompt, stale data, the densest screen.
5. Give gains, losses and a recommendation. The person who owns the product picks.

## 3. Craft rules

- **Type** creates role and rhythm. Check the languages the product ships in, numerals in columns, code or
  data where shown, and the fallback when the chosen face is unavailable. Honour user text-size settings.
- **Colour** names meaning. It never stands alone: pair it with a label, shape, position or icon. Define
  roles (surface, text, accent, danger, success) rather than hues, so light, dark and high-contrast themes
  share one meaning.
- **Spacing** groups related things and sets reading order. Unequal relationships get unequal spacing; a
  uniform grid of identical cards hides structure.
- **Borders, elevation and surfaces** show containment and focus, not decoration.
- **Motion** explains continuity, cause or a state change. Respect reduced-motion settings and never animate
  activity that is not happening.
- **Icons** come from one coherent family, with accessible labels and one stable meaning each.
- **Density** matches the work: generous where people browse, compact where they compare and scan. Do not
  inflate whitespace to look premium or cram to look powerful.
- **Every state is designed**: focus, pressed, selected, disabled, loading, stale, warning, error, success,
  and hover where the platform has a pointer.
- **Platform character**: follow each platform's conventions for system controls and typography scale; the
  brand lives in composition, type and detail, not in fighting the platform.

## 4. Things that fail on any product

Not style bans, but failures of meaning or access:

- essential text at low contrast;
- controls that appear only on hover, or only by a gesture nothing hints at;
- status carried by colour, pulse or animation alone;
- decorative metrics, fake activity or invented data;
- a component library's default look presented as the product's identity;
- marketing layout transplanted into a working screen.

## 5. Check

Look at real renders, not code or mock-ups, on each platform in scope: representative screen sizes and scale
factors, light and dark, largest text size, high contrast, reduced motion, a colour-vision simulation, the
longest translated strings and the densest data. Measure contrast against the current accessibility standard
for the platform; verify its current version before citing it.

Done when the accepted direction and the implementation captures match on every platform in scope, and
anything unverified is listed as unverified.
