# Identify the exact change

Use this protocol for assignment bases, Developer reports, review, QA, and delivery checks. A branch name or HEAD alone does not identify uncommitted content.

## Target identity

- For committed content, record the full base and target commit identifiers. Inspect the content at those commits; local working changes are not part of that target unless explicitly included.
- For local changes, record the base commit and a reproducible snapshot reference. The snapshot must preserve the actual target content: staged and unstaged changes, relevant untracked files, deletions, and binary files where applicable. A base plus a complete binary-capable patch and retained new-file content, or an immutable copy with a path/content manifest, can supply this evidence. Record a content digest and artifact location accessible to the reviewer. A digest without the underlying content is not reproducible.
- Include relevant configuration and dependency inputs for the checks. Exclude unrelated secrets and generated artifacts; identify any exclusions that limit verification. Without version control, use snapshots for both the base and target where available, and disclose missing baseline evidence.

Capture a stable target in an isolated copy or coordinate a pause in writes. Verify that captured content matches the intended target before checking it. Do not modify, stash, commit, or discard the user's work merely to obtain an identifier. If a stable snapshot cannot be obtained, report the target as unverified and leave its review or dependent closure pending.

## Evidence and delivery

Every check report names the exact target inspected or executed and the relevant environment. Checks on a moving working tree do not automatically apply to the captured snapshot. A later edit creates a different target even when HEAD is unchanged.

Before marking a ticket Done, compare the delivered content with the validated target. For a rebase, squash, cherry-pick, or other integration, record both identities and evidence that the delivered change matches the reviewed content, and assess changes to surrounding code, configuration, and dependencies. Matching commit labels, patch intent, or ticket IDs are insufficient. Repeat affected review and checks when behavior or its integration context changed, or when equivalence cannot be established. Preserve earlier results as historical evidence rather than transferring their approval silently.
