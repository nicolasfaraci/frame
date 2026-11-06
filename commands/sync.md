# Synchronize project documentation

## Inspect and propose

1. Identify the project root and authoritative copy, then resolve document paths using [documents.md](../references/documents.md). Preserve those paths and adapt links instead of creating default-path duplicates. Read the current version and documented changes in the [migration notes](../references/migrations.md). Read the baseline from `docs/.frame-version`. If the marker is absent or unrecognized, treat the baseline as unknown and assess the documents as they are. If the recorded Frame version is newer than the skill, report it and leave the project untouched.
2. Inspect the actual PRD, architecture, ADRs, optional design, backlog, and any archive. Compare their structure with the documented changes. Identify missing sections, outdated structures, and new requirements. Use version numbers to select candidate changes and concrete evidence in the files to decide what applies. Check the structure even when the version already matches.
3. Give the user a file-by-file plan. State the recorded baseline, target version, observed differences, exact edits or moves, preserved content, unresolved decisions, and planned log and marker changes. Identify completed and explicitly cancelled ticket IDs to move, preserving their distinct statuses. Flag ambiguities such as conflicting ticket copies or statuses. Stop for explicit approval of the plan. If the documents and marker already conform, report that outcome without edits.

## Apply the approved plan

1. Recheck the approved files for changes and confirm the authorized writer for the backlog and archive. If new discrepancies change the plan, bring the revised plan to the user before applying it.
2. Make targeted edits. Preserve business information, existing architecture decisions and ADRs, ticket IDs and statuses, criteria, and evidence. Keep existing documents and move complete ticket records using the [backlog protocol](../references/backlog.md). Any deletion of information requires explicit approval.
3. Verify the diff against the approved plan, check active and archived ticket IDs and statuses before and after, and check the table against active ticket details. Append a dated entry to `docs/FRAME-MIGRATIONS.md` with the original marker or unknown baseline, target version, and changes applied. On retry, reconcile partially applied changes and any existing log entry before continuing.
4. Write the current version to `docs/.frame-version` only after all approved changes required for conformance have been verified and logged. If work is partial or blocked, record any applied edits, report what remains, and leave the version marker as it was.
