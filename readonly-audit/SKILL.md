---
name: readonly-audit
description: Investigate a bounded question about a codebase, system, running service or incident through read-only evidence, and report coverage, findings and proof limits - what works, what only appears to, what cannot be proven. Changes nothing.
---

# Read-only audit

Answer one question from evidence without changing anything, and say exactly how strong each piece of
evidence is. The audit works on any system: an application or library, a mobile or web product, an
infrastructure setup, a data pipeline, a running service. Findings and recommendations are proposals; they do
not start work or stand in for anyone's acceptance.

## 1. Frame the question

Write down:

- the question, and the behaviour or contract the answer is measured against;
- the exact revision or version inspected, and any uncommitted changes present;
- what may be read, and which actions are excluded;
- whether this audits a specific delivery (with its acceptance criteria) or is an open assessment.

Done when a reader could repeat the audit from these four lines.

## 2. Keep it read-only

- Read sources, configuration, documents and retained evidence. Read tests as source.
- Do not run tests, builds, benchmarks, services, migrations, clean-ups or recovery. Do not edit, merge,
  commit, deploy or restart. Report needed changes as recommendations.
- Query a running system only when the question needs it and the query's side effects have been checked for
  the version in use. A command named `status`, `list` or `help` is not automatically safe. When no safe way
  to look exists, report the gap instead of trying an unproven command.
- Leave other people's in-progress work untouched, whoever it belongs to.
- Do not read credentials, tokens, private keys, raw production data or other secret-bearing files. Use
  sanitised views and non-secret metadata.

## 3. Follow the evidence chain

List the files and artefacts relevant to the question, then follow the dependencies as far as the claim needs.
List every file only when the audit is of the whole repository. Account separately for generated, untracked,
large and binary artefacts, and say what was excluded and why.

Trace the real path for the feature: entry point or surface → the logic that decides → the adapters and
external calls → the stored result → whoever consumes it, with the identity, permissions and configuration in
effect. Look at the failure, cancellation, retry, isolation and recovery paths too. Keep production wiring
apart from declarations, tests, mocks, fixtures and plans.

For each material claim, say which kind of evidence supports it:

- **Source evidence**: the behaviour is connected, or missing, at an exact revision. Tests were read, not run.
- **Retained execution evidence**: a test, run or capture was produced earlier, with its own revision,
  environment, time and scope. It was not repeated in this audit.
- **Current observation**: a safe look at a specific process, record or surface, with what it proves and what
  it leaves unproven. The checked-out code is not automatically the code that is running.
- **Unknown or not inspected**: the missing evidence, and the claim it prevents.

Check each important claim against a second source that is truly separate: the producer against the consumer,
the code against the stored record. Documents and summaries that copy one source are one source. Your own
cross-check is not an independent review.

## 4. Findings and uncertainty

Rate each capability, bound to the revision and evidence level:

- **works**: needs matching execution or surface evidence;
- **partly works**: name the proved part and the unproved part;
- **present in appearance only**: declared, displayed or tested, but not wired to a real effect;
- **does not work**: only with evidence of failure;
- **not proven**: missing access, a missing observation or an unrun test is not proof of failure.

Source wiring alone supports only a source-level conclusion. Absence of evidence is neither success nor
failure.

When the audit is of a specific delivery, mark each finding as blocking that delivery, related but not
blocking, or unrelated, against its actual acceptance criteria. Without such a delivery, group findings by
their relation to the question and their effect on users; do not invent a completion gate to fit the labels.

For a contradiction, name the sources, how fresh each is, and which one governs and why. When that cannot be
settled, mark the dependent conclusion as on hold and name the evidence or decision that would settle it. A
hold in the report changes nothing in the system and stops no unrelated work.

## 5. Report

Lead with the conclusion, in plain language. Then give:

- evidence by file and line or by record, with revision and observation time;
- coverage: what was inspected, counted by area, and what was skipped with the reason;
- findings and their effect on users;
- contradictions, holds and proof limits;
- facts, proposals, assumptions and unknowns kept apart, including evidence against the conclusion.

Explain confidence from the evidence; do not invent a numeric score. Leave out raw logs and large code dumps.
Finish with the recommended next decision or the evidence still needed.

Done when every claim in the report carries its evidence kind, and nothing in the system was changed.
