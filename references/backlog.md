# Backlog and concurrent edits

## One authorized session per project

Owning the backlog is a temporary assignment to write to it, separate from the roles. Only the authorized session writes to `docs/BACKLOG.md` and `docs/BACKLOG_ARCHIVE.md` in the authoritative copy of the project. This includes creating the files, assigning IDs, reserving tickets, and closing them. Subagents and other sessions submit proposals, even if each has its own branch.

- At the start, identify the authoritative copy and the authorized session. When only one session is working on the project, it can take on the assignment if the user asks it to write. When multiple sessions are involved or there is any doubt, the user designates one authorized session and tells it which copy is authoritative. Without a clear designation, stay in read-only mode and provide a proposal.
- Keep the same writer during parallel assignments. To hand off responsibility, the previous session stops writing and passes along the authoritative state and pending proposals. The new session then rereads the file and reservations before acting. If the previous session is unavailable, wait for the user to confirm that it has stopped writing and identify the copy to resume from.
- This rule is a coordination agreement. If other authors cannot follow it, suspend your edits and forward proposals to whoever controls the authoritative copy.

## Apply an update

1. Receive a targeted proposal with the ticket ID, revision or state observed, fields before and after the change, reason, and evidence. The PO triages agent findings and supplies the priority and rationale before they become follow-up work. For a new ticket, receive its title, criteria, and where it belongs. Only the authorized session assigns the ID. Check active, archived, and previously retired IDs before allocating it.
2. Reread the authoritative version just before writing and check for local changes. Apply a targeted edit that preserves the other tickets. If the ticket, reservation, criteria, or dependencies have changed since the assignment was issued, reassess the proposal against the current version. If a conflict remains unresolved, leave the ticket intact and report the discrepancy.
3. In the same update, check the summary table at the top of `docs/BACKLOG.md` against the active ticket details. Keep exactly one row per active ticket, with its ID, title, phase or epic, status, priority, and blocker or next action. Add the table from the [template](../templates/BACKLOG.md) if absent. Reconcile missing or stale rows within the authorized scope and report any other discrepancies to the PO.
4. Verify the diff, the ticket, and the summary row or archive entry. If the proposal has already been applied, confirm the state without duplicating an entry or event. If an operation was interrupted, reread both files and check the actual state of the assignments before retrying. Do not synchronize the backlog by merging a copy edited by a worker agent.

## Reserve and update a ticket

A ticket is ready when its scope and criteria are agreed on and its required dependencies are satisfied. The authorized session records the reservation and sets the status to `In progress` before implementation begins. Record the assignment ID, owner, write scope, base revision, and date. One reservation can cover multiple Developers with non-overlapping scopes. Before changing the status based on an older report, confirm that the report matches the active reservation. If the criteria change, tell the owner and confirm an updated assignment before the affected implementation work continues.

| Status | Condition |
| --- | --- |
| Needs refinement | The scope, criteria, or dependencies still need clarification. |
| Ready | The ticket is actionable, required dependencies are satisfied, and there is no active reservation. |
| In progress | A reservation is recorded for an authorized assignment. |
| Pending validation | The change is available at an identified revision and applicable checks are pending. |
| Blocked | A blocker is identified along with an action or condition for resuming. State whether the reservation remains active. |
| Done | The criteria have been verified and the change has been integrated or the result delivered according to the project process. For code changes, an independent Reviewer has approved the delivered revision or an equivalent change whose equivalence has been verified. QA is required when specified by the ticket or project. |

Statuses reflect actual progress. A fix can move a ticket back to `In progress`, and existing validation can make a formal transition through `Pending validation` unnecessary. Review and QA can work in parallel on the same revision. If behavior changes after validation, revalidate the affected areas before closing. Release the reservation at closure or after confirming that the relevant work has stopped. For each transition, record the date, assignment or role, reason, and available evidence. Mark unverified information as such.

## Archive or reopen a ticket

- On closure, record the `Done` transition, clear the active reservation, and write the full ticket into `docs/BACKLOG_ARCHIVE.md` under its phase and epic. Preserve the ID, criteria, evidence, and history. Create the archive from its [template](../templates/BACKLOG_ARCHIVE.md) if needed.
- When an approved migration moves a ticket already marked `Done`, copy its historical record as written. Flag an apparent active reservation or conflicting status to the PO for resolution before moving it.
- Verify that the archive entry is complete, then remove the active detail and summary row in one backlog edit. On retry, reconcile existing entries by ID and avoid duplicate records or transitions. Surface conflicting copies to the PO before removing either copy.
- Resolve ticket dependencies by ID across both files. Update known links affected by a move. Add the archive link at the top of the backlog once the archive exists and consult archived entries selectively during normal work.
- To reopen, restore the ticket with the same ID and history under the appropriate phase and epic. Record the reason and new status and restore its summary row. Verify the active copy before removing the archive entry.
