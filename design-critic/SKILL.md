---
name: design-critic
description: Review a design artefact - spec, mock-up, prototype or implemented screen, on any platform - with evidence-backed findings and a PASS / REVISE / NO-GO verdict.
---

# Design critic

Review design work against evidence and give a verdict that someone can act on. This works for any product
and surface: mobile, web, desktop, terminal, voice, embedded. It judges the work against the product's own
accepted direction and its users' needs, not against the reviewer's taste.

## 1. State the role and the artefact

- **Role.** An independent verdict needs a reviewer other than the person or agent that made the work.
  A second look by the maker is a self-review: it reports findings and gives no independent PASS.
- **Artefact.** Name whether this is a specification, a mock-up, a prototype or an implemented surface, and
  its exact version. The verdict covers that artefact only; approving a prototype does not approve the
  product.
- **Scope.** Review-only means no fixes and no edits.

## 2. Gather the inputs

- the product's accepted direction and any binding brand or design decisions;
- the real artefact;
- the states and data it shows, and where that data comes from;
- screenshots, recordings or terminal captures under representative conditions;
- interaction, accessibility and test evidence;
- known dependencies and who owns what.

When evidence the claim needs is missing, do not guess PASS.

Done when each claim to be reviewed has an artefact and evidence, or is marked as unevidenced.

## 3. Rubric

Apply each lens that is relevant; say which were skipped and why.

1. **Truth.** No invented capability, state, number or permission.
2. **Workflow.** The main job can be completed; the primary decision and the next safe action are obvious.
3. **States.** Empty, loading, partial, stale, error, permission-limited, offline and recovery are designed.
4. **Hierarchy.** Order and emphasis follow what matters to the user.
5. **Visual language.** Consistent with the accepted direction; meaning is not carried by decoration.
6. **Interaction.** Every input the platform offers works; focus, interruption and destructive actions are
   coherent.
7. **Accessibility.** The current standard for the platform (for example WCAG and the vendor's guidelines):
   contrast, text scaling, assistive technology, reduced motion, non-colour cues. Verify the current version
   before citing it.
8. **Platform fit.** Follows the conventions of each platform in scope; departures have a stated reason.
9. **Text and languages.** Real strings, room for longer translations, right-to-left where supported.
10. **Multi-user concerns**, where the product has them: scope, permissions, audit, cost, tenant separation.
11. **Feasibility.** Buildable on the existing architecture; performance and migration considered.
12. **Evidence.** Real rendered behaviour, not intent or a mock-only claim.

## 4. Finding format

Each finding carries:

- an ID and severity: BLOCKER, HIGH, MEDIUM or LOW;
- the surface, workflow and exact state;
- the evidence: a file, capture, behaviour or the missing proof;
- the rule or contract it breaks;
- the effect on the user or on operation;
- the smallest lasting fix;
- the check that would close it.

No taste-only language such as "feels off". State the observable problem and its consequence.

## 5. Verdict

- **PASS**: no BLOCKER or HIGH finding; critical states and target environments have credible evidence;
  nothing claims to be finished that is not; lower findings are stated as non-blocking.
- **REVISE**: the direction works, and one or more material problems must be fixed before acceptance.
- **NO-GO**: the design shows something untrue; a permission or tenant boundary is unsafe; a core workflow
  or its recovery is missing; it contradicts the accepted direction; accessibility blocks the main job; it
  depends on something that does not exist; or the evidence is too thin to judge a critical claim.

## Output

    ROLE: independent reviewer | maker's self-review
    ARTEFACT: kind and exact version
    VERDICT: PASS | REVISE | NO-GO   (a self-review lists findings without an independent PASS)
    SCOPE: surfaces, states and evidence reviewed
    FINDINGS: ordered by severity
    EVIDENCE GAPS: what could not be judged
    STRENGTHS: only those backed by evidence
    TO CLOSE: the exact checks needed for the next verdict

Do not soften a blocking finding with a numeric score.
