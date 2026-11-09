---
name: authority-bootstrap
description: Session start, resume after compaction or handoff, or a changed instruction - take a read-only snapshot of what was asked, what is permitted, the workspace state, who owns unfinished work and how fresh the evidence is, before acting. Also for "where were we", "pick this up", "continue from the handoff".
---

# Authority bootstrap

Establish where you stand before doing anything. An agent that resumes from a summary, a handoff note or an
old transcript tends to act on stale permission and a stale picture of the workspace. This skill produces a
short, read-only snapshot that fixes both. It works in any project: code, documents, data, operations.

A session start is not something a person types, so an agent that picks skills by matching the request will
often miss this one exactly when it matters. Where the agent supports a session-start hook, wire the skill to
it; the repository README has a recipe.

Taking the snapshot changes nothing and grants nothing. Reading a document, receiving a message or holding a
snapshot is not permission to start work.

## 1. When to take or refresh it

Take it at session start. Refresh the affected parts, not the whole snapshot, when any of these happens:

- the person gives a new or changed instruction;
- a permission is granted or withdrawn;
- the working directory, branch or revision changes;
- another agent or person starts working on the same files;
- the session resumes after compaction, a handoff or a long pause;
- configuration that the task depends on changes.

Reuse what has not changed; do not reload every source before each small step.

## 2. Establish instructions and scope

- Find the live instruction from the person directing the work, then the project's standing instruction files
  and the documents they point to. Newer and more direct wins; note any conflict instead of resolving it
  silently.
- Identify the exact objective that was accepted, your role, what you may read and write, which actions are
  permitted, and which decisions still belong to the person.
- Tell apart: an instruction, an accepted plan, something already built, an old record, and something you
  observed just now. A proposal, a finding or a to-do list is not an accepted task.
- A previous transcript, a summary or a handoff note describes the past. It does not replace the current
  instruction or current verification.

## 3. Establish the workspace

- Identify the actual working copy and its revision or version.
- Record what is changed, staged and untracked, and whether other copies or sessions overlap with your paths.
- Do not guess who owns an unexpected change from its filename or location. Mark it as unknown ownership and
  leave it intact.

## 4. Look at running systems only when the task needs it

For work that only edits files, report the running system as not inspected. When the task makes a claim about
a running system:

- identify the actual installation, its configuration and the identity and permissions in effect;
- separate the checked-out source from the version actually running; they are often different;
- use only queries whose side effects you have checked. A command named `status`, `list` or `help` is not
  automatically read-only;
- do not start, build, migrate, clean or repair anything as part of the snapshot;
- do not read credentials, tokens, private keys or raw private data; use sanitised views;
- when no safe way to look exists, report the gap instead of guessing.

A process listing or a cheerful status line does not prove that something ran or finished.

## 5. Handle uncertainty without changing anything

Record conflicting sources with their date or revision, and which one governs and why. When permission,
freshness or ownership cannot be settled, put the dependent action on hold in the report and name what would
settle it. Continue with unrelated permitted work. Keep four labels apart: not inspected, unavailable,
unknown, verified. Absence of evidence is neither success nor failure.

## Output

A short, timestamped snapshot in plain language:

- sources read, with their revision or date; the working copy and any changes of unknown ownership;
- the accepted objective, your role, permitted actions and paths, and decisions still pending with the person;
- what was verified, what was observed of running systems, and what is uninspected, unavailable or unknown;
- contradictions and holds, each with the evidence or decision that would resolve it;
- the exact next permitted action.

Do not invent timestamps, actors, approvals or results. Finishing the snapshot does not satisfy the next
action's own requirements.
