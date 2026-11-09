---
name: parallel-execution
description: Split work across several AI agents or sessions running at once and merge the results - lane briefs, disjoint write ownership, one writer per workspace, supervision, fan-in order and conflict rules.
---

# Parallel execution

Run several agents on one goal without them overwriting each other or handing back results nobody can trust.
This applies to any mix of agents, models and tools, and to any kind of work with files: code, documents,
content, data. It decides how lanes are cut, briefed, supervised and joined; it does not grant permission to
start agents. That comes from the person directing the work.

## 1. Decide whether to split at all

Split only when the pieces are truly independent, there is a real point where they join, and the time gained
outweighs the cost of coordinating. A small or tightly coupled task gets one writer. The number of lanes
follows the dependency structure and what the machine and the budget can carry, never a fixed habit.

Done when each lane has a responsibility that can be finished and checked without waiting on another lane, or
the task is kept whole.

## 2. Lane brief

Each lane gets a written brief. The agent knows nothing the brief does not say.

- the starting point: exact revision or version of the inputs;
- the task and the result expected;
- what it may read, what it may write, and what it must not touch;
- that it is the only writer of its paths;
- what to hand back: the changed files, and the evidence of what was checked;
- limits on time, cost and retries, and when to stop and report;
- what it may not do: merge, publish, deploy, or change shared settings.

Put what is common to all lanes in one shared brief and keep the per-lane part short.

Done when no two briefs list the same writable path.

## 3. Lane rules

- **One writer per workspace.** Give each lane its own working copy (a branch and worktree, a folder, a
  sandbox). Before starting, check nothing else is writing there. A separate working copy prevents collisions;
  it does not isolate processes, network access or secrets.
- **Shared heavy resources take turns.** Builds, full test runs, ports, databases and rate-limited services
  go through one lock or queue, so lanes do not starve or corrupt each other.
- **Match the lane to what the agent can do.** An agent whose sandbox cannot run something (a network test, a
  device, a GUI) hands that check to the coordinator with exact instructions; it does not claim it passed.
- **A report is not verification.** A lane's own summary is a claim. Evidence is the diff and the output of
  checks actually run.
- **Failures come back as new work**, with the real error, not as an instruction to try again.
- **Keep provenance.** For each lane keep its starting revision, its diff and its check output. Never
  fabricate a result, a receipt or an approval.

## 4. Supervise

Look at what each lane produced, not only at what it says it did. Stop a lane that runs past its limits,
repeats the same failure, or wanders outside its paths. Pause the affected lane when permission is missing, a
conflict appears or its budget is spent; let unrelated lanes continue.

## 5. Fan in

- Join on one branch or copy, in dependency order.
- At each join recheck: the base each lane started from, overlapping writes, and that the result belongs to
  this lane and this run. Reject results that are stale, duplicated, from another run or of unclear origin.
- **Shared registry files** that every lane appends to (translation catalogues, route or error tables,
  indexes, changelogs) are merged as the union of both sides, never by taking one side.
- Run the checks again on the joined result. Lanes passing alone do not prove the whole works.
- Keep three things separate: the maker's own checks, an independent review, and acceptance by whoever owns
  the result. A lane never approves its own work.
- Bound retries. An unchanged failure, or a side effect that may or may not have happened, does not justify
  another automatic attempt.

Done when the joined result passes its checks and every rejected or deferred lane result is listed with its
reason.

## 6. Deliver

Report each lane's inputs and outputs, the exact joined change, the evidence at each join, checks and
failures, open limits and the next step. Do not clean up shared state, force a result through or restart
services as part of coordination.
