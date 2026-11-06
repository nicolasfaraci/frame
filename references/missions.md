# Modes and assignment protocol

## Interactive

Take on a role for the current exchange. Read its instructions and the relevant context. A PO discussion can produce proposals while a separate workspace handles tickets that are already reserved. When the user asks to record a decision, follow the writing rules for the relevant document.

## Delegated

The PO coordinates this protocol in the orchestrating session. Each temporary agent works within its brief and returns its report to the PO for triage. The PO routes validated backlog proposals to the authorized writer and decisions requiring human input to the user.

1. Identify the explicitly authorized assignments and available native tools. Use temporary agents with fresh context where possible. The same instructions can be passed to another session opened by the user.
2. For each implementation assignment, verify dependencies and reserve the ticket through the [backlog protocol](backlog.md). Assign exclusive files or modules and record the exact base revision, including dependencies already integrated. For simultaneous edits, use separate working copies if the host supports them. If a dependency, shared file, or lack of isolation prevents safe separation, sequence only the assignments that conflict. Before launching the next assignment, verify that its base includes the changes it depends on and that the write conflict is resolved. Read-only assignments can proceed against an identified revision.
3. Launch only assignments that are ready and explicitly requested. Pass along the relevant instructions, since a subagent may not inherit the skill or local changes. Verify that it can see the required revision and files. When results arrive, inspect the diffs and evidence. Have the person or session authorized by the project integrate the changes within the requested scope. Agents do not push or merge on their own initiative.
4. If a launch fails, confirm whether the agent exists before retrying. If the outcome is uncertain, keep the reservation and report the situation. If the failure is confirmed, the authorized session can release the reservation or record the blocker. If an agent stops, collect available results and state which checks are still needed before resuming.

### Assignment brief to hand off

~~~markdown
- Role and objective
- Ticket(s), expected result, criteria, and dependencies
- Project root, working copy, and reference revision
- Documents and sections to read, relevant ADRs
- Files that may be edited and shared areas to avoid
- Role constraints, including read-only access to docs/
- Expected checks, stopping conditions, and report format
~~~

### Expected report

~~~markdown
- Ticket, role, base revision, and revision reviewed or produced
- Result, changed files, and diff reference where applicable
- Checks actually run and their results
- Risks, blockers, and remaining checks
- Proposed ticket update with fields and evidence
~~~

## Host capabilities

Launch through the native tool exposed in the session and follow its permissions and isolation mode. If the session has to wait for results, state that limitation. If the user wants to continue the PO discussion in that case, they can use a separate session with an up-to-date copy and the same writing protocol. Launching, continuing in the background, and resuming work all depend on the host capabilities you can verify. If no tool is available, provide briefs ready to hand off and keep ticket statuses aligned with actual progress.
