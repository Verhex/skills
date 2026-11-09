---
name: beuser
description: Write the journey spec before building anything a person or company uses, and walk it on the assembled product afterwards - AI agents act as the persona on a real instance (app, web, CLI, API, device), walk every branch and give the acceptance verdict.
---

# BeUser

A surface is accepted when the person's whole journey works on the assembled product, not when each piece
passes its own tests and review. This skill has two halves: a journey spec written before building, and a walk
by AI agents acting as the persona after the pieces are joined. It works for any surface a person meets: a
mobile or desktop app, a website, a command line, an API, a voice or chat interface, an installer, a device.

The walk is evidence for whoever accepts the work. It is not their acceptance, and it grants the walker no
permission it did not already have.

## 1. Journey spec, before building

Write this as part of the plan, before code:

- **Personas.** The real range of people who will use the surface, from the least experienced to the expert,
  and for an organisation its roles (administrator, member with limited rights). Each with goals, skill
  level, device and setting, language, and tastes: wording, density, order.
- **Starting states, each a branch.** First use, returning use, an earlier attempt that failed or stopped
  halfway, an older version, a missing permission, no network, a slow device, an expired session.
- **Per step.** What the person sees or hears, each choice available, the outcome, and every refusal or error
  with its cause and the exact next step it offers.
- **Twin paths.** Where the same job can be done more than one way (a menu and a command flag, a screen and
  an API call, touch and keyboard), list both and the points where they must agree.
- **Borrowed shape.** Name the proven product that does the same job and the behaviour copied from it. Mark
  what no proven product covers; those steps carry the most risk.

Done when every branch has a starting state, choices, an expected outcome and next steps for each refusal,
and the twin-path table has no gap.

## 2. Walk, after the pieces are joined

- **Target the assembled product.** The build with all the planned pieces merged, never one piece in
  isolation. Record the exact version or revision.
- **Use a disposable instance the walker owns.** A fresh install, a test account, an emulator or a staging
  environment created for the walk, where the walker is the persona and nothing real can be harmed. Shared,
  production or customer systems are for read-only observation, and only when that has been permitted.
- **Drive the real thing.** The real binary in a real terminal session, the real page in a browser, the real
  app on a device or emulator, the real endpoint. No mocks, no calling internal functions directly.
- **One brief per walker.** Persona, goals, skill level, tastes, the journey spec, the instance and what the
  walker may do on it, and where the transcript goes. The walker behaves as that person would: it reads what
  is on screen and does not use knowledge of the code.
- **Prefer a walker that did not build it.** A different model or agent than the author sees what the author
  cannot. When none is available, say so in the report.
- **Walk every branch and both twin paths.** Per step record the input given, what the surface showed
  (trimmed), confusion, dead ends, wrong or missing next steps, and taste notes.
- **Verdict per branch.**
  - GREEN: outcome as specified, nothing confusing.
  - FRICTION: outcome reached, with a clarity or taste finding.
  - RED: wrong outcome, dead end, refusal without a usable next step, or data at risk.
  - UNWALKED: not walked, with the reason.
- **Keep the transcript and the verdict table** with the exact version they belong to.

Done when every branch has a verdict tied to the exact version.

## 3. Acceptance and findings

- Done means every branch walked GREEN on the assembled product, including the steps only a person performs.
  FRICTION is fixed or explicitly accepted by whoever owns the product. RED and UNWALKED block.
- Automated tests guard against regressions and stay required. They are not the acceptance model, and a large
  test run never replaces the walk.
- A finding is fixed before acceptance, then that branch and its neighbours are walked again on the new
  build. It is not pushed to a later release.
- The person who accepts reads the report; they do not have to walk.

## Safety

- The walker acts as the person only inside its own disposable instance, and labels those steps as synthetic.
  A synthetic step is never evidence that a real person approved something.
- On every other system the walker never bypasses a sign-in, consent, approval, payment or policy step, and
  never acts as a real person.
- Destructive actions (delete, uninstall, reset, purchase, send) happen only in the disposable instance.
- No secrets, tokens, keys or private content in transcripts; redact before keeping them.
- Bound each walk in time and retries. When an action's effect is uncertain, stop and report instead of
  trying again.
