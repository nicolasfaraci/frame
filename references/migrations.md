# Documentation versions

The current version is `1.0.0`. Store this version as a plain line in `docs/.frame-version`. Increment it when the project documentation conventions change and record each change here with the evidence that makes it applicable.

## 1.0.0 — Frame

Use the observed structure of an existing project's documentation to determine which changes apply.

| Observed structure | Change |
| --- | --- |
| Active backlog without a summary, or summary fields out of sync with ticket records | Add or reconcile the active ticket summary from the [template](../templates/BACKLOG.md). Derive values from existing records and flag gaps. |
| Missing archive or `Done` / explicitly `Cancelled` tickets in the active backlog | Create the archive as needed and move each full terminal ticket using the [backlog protocol](backlog.md). Keep IDs, statuses, links, and evidence. |
| Missing core sections or documents that the current templates require | Propose only the missing pieces and use available project evidence. Leave unknown business or architectural decisions open. Optional design and individual ADRs remain conditional. |
| Missing or unrecognized Frame marker | Record an unknown baseline and the applied changes in `docs/FRAME-MIGRATIONS.md`. Write the Frame marker after verifying conformance. |

Resolve and preserve existing document paths using [documents.md](documents.md), including the backlog and archive. Adapt links when creating missing documents.

These are the initial `1.0.0` conventions. Also inspect these cases even when the marker already reads `1.0.0`:

| Observed structure | Change |
| --- | --- |
| Verification records identify only HEAD despite known local changes | Flag the target as unverified; preserve historical evidence and establish an exact target for current work using [revisions.md](revisions.md). Never invent a historical snapshot or approval. |
| Cancelled tickets lack cancellation details or have an apparent active reservation | Preserve the recorded status and evidence; resolve shutdown and decision gaps before archival. Do not infer cancellation from blockage or inactivity. |
| Archive or summary assumes every terminal ticket is completed | Preserve each terminal status and distinguish cancelled work from completed work. |
