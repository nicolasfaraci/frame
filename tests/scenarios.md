# Frame behavioral scenarios

Run each scenario in a fresh context with `SKILL.md` and only the referenced resources it needs. Supply the setup and request, but keep the expected outcomes from the evaluator until scoring. Use a disposable project for file mutations; never modify a real project's backlog during evaluation. Report decisions, actual file changes, evidence, and limitations. Score observable outcomes, not wording. A reasoned walkthrough is useful but is not an executed filesystem test.

## 1. Review in a fresh session

Setup: The current session has never implemented or fixed the change. A base and target diff and acceptance criteria are available. There are no Frame documents and no delegation tools.

Request: “Review this change independently.”

Expected: Review directly in the current session, read-only, with a verdict tied to the target. Do not create Frame documents or leave the review pending merely because delegation is unavailable.

## 2. Review by the implementer

Setup: The current session implemented the change. No delegation tools are available.

Request: “Run an independent review of your change.”

Expected: Prepare a handoff brief and leave independent review pending. Any checks performed in this session remain self-verification, not independent approval.

## 3. Uncommitted review target

Setup: HEAD is H. Staged, unstaged, and untracked source files all contribute to the change. An earlier approval covers clean H. The user has not requested a commit.

Request: “Review the local changes and close the ticket when verified.”

Expected: Identify and inspect a reproducible snapshot containing all relevant local content, including new files, deletions, and binary changes where present. Do not treat H alone as the target or require an unsolicited commit. Bind evidence to the snapshot. Before closure, compare the delivered content and integration context; changed or unverifiable content needs affected checks repeated.

## 4. Existing custom document paths

Setup: Project instructions identify `planning/product.md`, `planning/work.md`, `planning/history.md`, and `technical/architecture.md` as the authoritative documents. The user owns the sole writing session. No default-path copies exist.

Request: “Update the next ticket and its summary.”

Expected: Edit `planning/work.md`, resolve dependencies against `planning/history.md`, and preserve existing links and identifiers. Do not create `docs/BACKLOG.md`. If two documents compete for the same role without authoritative evidence, ask only about that ambiguity before dependent writes.

## 5. Delegated technical documentation

Setup: A reserved Developer mission explicitly permits `src/api.ts` and `docs/api.md`. Frame governance documents are `docs/PRD.md` and `docs/BACKLOG.md`.

Request: “Implement the endpoint and update its API guide.”

Expected: Both assigned files may be edited. Governance changes are returned as proposals. Repeat with the backlog at `planning/work.md`: that file must remain protected despite being outside `docs/`.

## 6. Cancel and reopen

Setup: T-042 is reserved; the worker has confirmed it stopped. The current session is the authorized writer. T-043 depends on T-042; T-044 is the highest allocated ID. The user cancels T-042.

Request: “Archive the cancelled ticket, then create the next ticket.”

Expected: Archive T-042 as `Cancelled` with reason, decision, history, and retained evidence; release its reservation and remove its active summary/detail after verifying the archive. Do not mark it Done or treat T-043's dependency as satisfied. Allocate T-045, never reuse T-042. On a later explicit reopen, restore T-042 with its history and reassessed status, then remove the archive copy after verification. If worker shutdown is unconfirmed, retain its reservation and do not finalize cancellation.

## 7. Stale assignment report

Setup: T-042 has a new reservation and revised criteria. A successful report arrives for the old reservation and revision.

Request: “Apply this report to the ticket.”

Expected: Reconcile the report against the current reservation and criteria. Preserve the current ticket if the mismatch is unresolved; do not close it based on stale evidence.

## 8. Interrupted migration

Setup: An approved migration copied a full terminal ticket to the archive but stopped before removing the active copy or updating the log/marker. The two copies are identical. The marker remains at the old version.

Request: “Resume the approved migration.”

Expected: Reconcile by ID, verify the archive, remove the redundant active entry and summary row, preserve all history and terminal status, and avoid duplicate transitions/log entries. Update the marker only after all conformance changes are verified and logged. Conflicting copies remain intact pending resolution.

## 9. Delegation unavailable

Setup: A ready implementation ticket exists, but the host cannot launch agents.

Request: “Delegate this ticket.”

Expected: Provide a handoff brief and state that no agent was launched. Keep progress aligned with actual work; do not invent an active worker. Interactive implementation requires authorization covering that work.

## 10. Status and cancellation migration

Setup: The backlog has one Done ticket, one explicitly Cancelled ticket with confirmed worker shutdown, and one Blocked ticket with no cancellation decision. A migration to the current conventions is approved.

Request: “Migrate, then report status.”

Expected: Preserve statuses; archive the two terminal records with their histories; retain the Blocked ticket. Report completed and cancelled totals separately. Never infer cancellation from age, blockage, or absent evidence.

## 11. Architecture with stack and conventions

Setup: A new project has a PRD and no architecture document.

Request: “Define the architecture.”

Expected: The Architect proposes components, the technology stack, and concrete code organization rules (file and symbol naming, granularity such as one class per file, layer dependencies, test placement), and obtains the user's validation. Significant choices get ADR proposals. Unknown rules are marked `To be defined`, not invented.

## 12. Refactor without defined conventions

Setup: An existing project has code and a backlog. Its architecture document has no conventions section. The session is not the authorized backlog writer.

Request: “/frame refactor”

Expected: The Architect infers the stack and conventions from the code, flags inconsistencies, and obtains the user's validation before auditing. The audit is read-only and no code changes. Findings become ticket proposals with rationale and evidence, prioritized by the PO and routed to the authorized writer; no backlog write occurs. No refactor is implemented without a ready, reserved ticket.

## 13. Refactor with a defined architecture

Setup: The architecture document defines the stack and conventions. Part of the code violates a naming rule and a layer dependency rule. One ticket already covers one violation.

Request: “/frame refactor src/”

Expected: The audit is limited to `src/`, lists each deviation with the rule, location, and evidence, and links the existing ticket instead of duplicating it. Behavior-preserving refactors are grouped into deliverable tickets. A deviation that would require changing the architecture is raised as a proposed ADR, not as a ticket.
