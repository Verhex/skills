---
name: agentic-ux
description: Design how a product shows and controls AI agent or automation work, on any surface (chat, app, web, terminal, voice, notification) - task and step state, tool calls, approvals, autonomy levels, pause/resume/cancel, failure and human takeover. Use for "design the agent run view", "how should approvals look", "show what the agent is doing".
---

# Agentic UX

Make autonomous work legible, controllable and recoverable without pretending to a certainty the system does
not have. This skill covers what the interface must tell the truth about. Layout, styling and platform
conventions are separate decisions, and no particular surface or framework is assumed.

## 1. Start from what the system really does

Read the product's actual model before designing: what units of work exist (a task, a run, a step, a tool
call), how they nest, which states each can be in, and what moves one state to the next. Design only on states
and controls the system has. A control the backend cannot honour is labelled a dependency, not drawn as a
working button.

For every object shown, determine:

- who or what started it;
- which person, permission and scope allowed it;
- its current state and how old that state is;
- which agent, model or service is responsible;
- its input, output and side effects;
- cost, usage and limits, when available;
- what has been verified and how;
- what the person can do about it and what that will cause;
- how it recovers, and what history is kept.

Done when each displayed object answers these from the real system, with gaps listed.

## 2. State matrix before any component

| Axis | Values to resolve from the real system |
|---|---|
| Lifecycle | queued, accepted, active, paused, blocked, finishing, ended |
| Freshness | live, delayed, stale, disconnected, unknown |
| Permission | allowed, approval needed, denied, expired, unavailable |
| Evidence | pending, partial, verified, contradicted, unavailable |
| Outcome | success, failure, cancelled, replaced, partial, effect unknown |

Never fold unknown, stale, unavailable and failed into one warning state.

## 3. Trust rules

- Show the chain: what the person asked → the plan → the action → its side effect → the evidence.
- Keep four things visibly apart: what the model proposed, what policy decided, what a tool did, what was
  verified.
- Leaving or closing a view never implies the work stopped.
- Pause, resume, cancel, retry and undo each state exactly what they affect and what may already have
  happened.
- An approval request shows who is asking, the action, the resource, the scope, how long it lasts, the risk
  and what follows.
- A denied or expired approval leaves a way forward; it does not vanish.
- Streaming output stays navigable and ends in a stable final record.
- Optimistic display never invents a finished success.
- Background work shows its freshness and last known state, and stays findable after the person moves away.

## 4. Levels of human involvement

Design at least these, and say which the product actually supports:

- observe only;
- guide or correct;
- approve one bounded action;
- pause at a safe point;
- cancel, with the partial side effects stated;
- retry from a defined checkpoint;
- take over manually.

How much the agent does unasked is the person's choice, set where they can see and change it. Every
intervention keeps a record of who did what.

## 5. Failure and recovery

For each critical action, cover: timeout, lost connection, service unavailable, insufficient permission, budget
or limit reached, partial side effect, failed verification and a conflicting action by someone else. State
what is safe to retry and what must be checked first. An effect that may or may not have happened stays shown
as unknown until the system confirms it; the interface cannot settle it by assumption.

## 6. Fit each surface

The same truth appears on every surface the product has; the form follows the surface.

- A chat thread carries causality in order and approvals inline.
- A dense app or web view can show many units side by side with drill-down.
- A phone favours one unit at a time, with notifications for decisions that cannot wait.
- A terminal relies on text hierarchy and keyboard control.
- Voice states the action and consequence aloud and confirms before anything irreversible.

A surface may leave out an interaction only when it says so and points to where it can be done. Changes that
happen on their own are announced to assistive technology without flooding it.

## Output

- the object and lifecycle model, grounded in the real system;
- the state and transition matrix;
- the approval and intervention contract;
- the evidence and attribution model;
- the failure and recovery matrix;
- the mapping to each surface in scope, with accessibility announcements for live changes;
- the gaps where the backend prevents an honest interface.

A handsome timeline with invented state transitions is a failed design.
