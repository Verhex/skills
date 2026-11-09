---
name: enterprise-ux
description: Design governance and administration surfaces - organisation and resource scope, users and roles, permissions, policies, approvals, audit logs, secrets, budgets and cost limits, bulk administration - in any product and on any surface, without degrading the single-user experience.
---

# Enterprise UX

Make governance understandable and safe at large scale without making the product worse for one person using
it alone. This applies to any product that has more than one user or any rule about who may do what: a SaaS
admin console, a mobile app's team settings, a command-line tool's policy commands, an internal platform.

## 1. Resolve the real authority model

Before designing a control, establish from the product's actual implementation:

- the scope levels that exist (for example organisation → unit → project → resource), and which are
  implemented versus planned;
- the kinds of actor: people, service accounts, automations, agents;
- which roles and policies are inherited and which are set explicitly;
- what a permission is scoped by: resource, action, time, environment;
- where a permission decision is actually made and by what;
- what is recorded for audit, and how long it is kept;
- what isolation between organisations or tenants the system really guarantees.

Visual nesting never stands in for real authorisation. A persona, a job title or an organisation label grants
nothing; only the system's effective permission does. Do not add a second approver, or any other ceremony,
merely because the customer is large; require it only where an explicit policy asks for it.

Done when each control in the design points to the real rule that enforces it, and unenforced ones are listed.

## 2. Interaction rules

- Show the effective permission and why it applies, including what was inherited and which deny won.
- A policy preview or simulation is clearly not in force until applied.
- An approval request shows who asks, the resource, the action, the scope, the duration, the risk and what
  follows.
- A bulk action shows what is selected, what is excluded, what happens if part of it fails, and what cannot
  be undone.
- Secrets show metadata and lifecycle, never the value.
- Cost views tell observed usage, estimate, budget, hard limit and provider-reported figures apart.
- Differences between environments are visible before something is deployed or run.
- Audit records cannot be edited from the interface, can be filtered, and link to the related evidence.
- Acting as another user or with delegated rights is unmistakable, bounded and logged.
- Export respects redaction, permission and tenant boundaries.

## 3. State matrix

Cover each that applies:

- allowed, denied, approval needed, expired, policy unavailable;
- policy inherited, overridden, conflicting, shadowed;
- account provisioned, invited, suspended, removed, orphaned;
- credential active, rotated, expiring, revoked, inaccessible;
- within budget, forecast at risk, limit reached, provider figures unavailable;
- bulk action partly succeeded, a retryable subset, reconciliation needed.

Unknown is never shown as allowed.

## 4. Scale

Large sets need server-side paging or streaming, stable sort, search, filters, saved views, clear
bulk-selection meaning ("these 50" versus "all 12,000 matching") and export limits. A count says whether it is
exact, sampled or delayed. A long-running administrative operation shows progress, partial results and
recovery like any other long-running work.

## 5. Keep the single user whole

Governance appears when it is relevant. A person working alone sees no organisation chrome, empty role lists
or approval steps that only they could approve. The same product grows into its governance; it does not become
a second product.

## 6. Comprehension and accessibility

Use plain language beside the exact policy identifier. Tables and trees work fully with each input the
platform offers; focus stays stable after a change; risk is never carried by colour alone; diffs are readable
by assistive technology; dates, numbers, currencies and time zones follow the viewer's locale and state their
zone.

## Output

The scope and actor model; the effective-permission explanation; approval and policy flows; the audit and
evidence model; secret and cost handling; the adverse-state matrix; behaviour at scale; and what must be
proven about tenant isolation. A generic admin dashboard without these is a failed design.
