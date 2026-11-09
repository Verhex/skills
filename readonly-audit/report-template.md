# Audit report: filled example

An invented question about an invented service, to show the shape. Replace every line with your own facts.

## Question

Does the "export my data" feature deliver a complete export to the user, as the privacy page promises?

- **Measured against:** the privacy page ("a full copy of your data within 24 hours") and the feature's spec.
- **Inspected:** revision `9b1e77a`, no uncommitted changes.
- **Read boundary:** the repository and last week's job logs. Nothing was run. No user data was opened.
- **Kind:** open assessment, not the audit of a specific delivery.

## Conclusion

The export is **partly working**. The request, the job and the download link are connected end to end.
Attachments are not included: the job collects them into a list that nothing reads.

## Evidence

| Claim | Evidence kind | Where |
|---|---|---|
| The button creates an export job | Source | `web/settings/export.tsx:41` → `api/export.ts:18` → `jobs/export.ts:9` |
| The job writes profile, notes and comments | Source; tests read, not run | `jobs/export.ts:22-58`, `jobs/export.test.ts` |
| Jobs completed last week | Retained execution | job log 3–9 June, 212 completed, 0 failed, running revision `8c0d412` |
| Attachments are missing from the archive | Source | `jobs/export.ts:61` builds `attachmentPaths`; no later line uses it |
| The link expires after 24 hours | Source | `api/export.ts:47` |
| Exports arrive within 24 hours | Not proven | the log has completion times but no request times |

Second source for the main finding: the archive writer `lib/archive.ts:12` accepts only the three record
types, which agrees with the job.

## Coverage

- Inspected: 9 files in `web/settings`, `api`, `jobs`, `lib`; 1 test file; 7 daily job logs.
- Skipped: the email template (outside the question), generated API client (generated from `api/`).
- Note: the logs come from revision `8c0d412`, one commit behind the inspected source. That commit touches
  only documentation.

## Findings

| Capability | Rating | Effect on users |
|---|---|---|
| Request and download an export | works (source and retained runs) | none |
| Export contains all data | present in appearance only, for attachments | users receive an incomplete copy while the page promises a full one |
| Delivery within 24 hours | not proven | unknown |

## Contradictions and holds

The privacy page says "full copy"; the code exports three of four data types. The code governs what happens;
the page governs what was promised. **On hold:** any statement that the feature meets the privacy promise,
until attachments are included or the page is changed. That is a product decision.

## What decides the rest

1. **Settled from source:** request → job → archive → link is connected; attachments are not exported.
2. **Settled from existing records:** jobs complete without failures at the current volume.
3. **Needs an active check:** whether a real export downloads and opens (run one export on a test account
   and open the archive); whether exports finish within 24 hours (compare request and completion times, which
   needs request times added to the log or read from the job table).

## Recommended next decision

Decide whether attachments belong in the export. Either answer needs a change: to the job, or to the privacy
page. This audit proposes; it changed nothing.
