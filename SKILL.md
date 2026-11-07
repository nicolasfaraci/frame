---
name: frame
description: "Use when the user wants to work with a temporary software team, discuss product scope with a PO, manage a backlog, make architecture decisions, delegate ready tickets in parallel, request independent review or QA, explicitly engage a Designer, or initialize, migrate, or inspect team project documentation."
---

# Frame

Choose the requested role and mode. Each assignment uses a temporary role with a defined objective. The conversation can move from PO to QA or cover several independent tickets. Use the project's authoritative documents to pick up where work left off.

## Route an optional command

On explicit invocation, check for a standalone command word immediately after `$frame` or `/frame`. If the host supplies the invocation text separately, check the first word of that text. Match one of the five exact words below, then pass the remaining text as context and read only the matching command file. Follow that command's workflow and load shared references only as needed.

| Command | Workflow |
| --- | --- |
| `init` | [Initialize project documentation](commands/init.md) |
| `sync` | [Plan and apply a documentation migration](commands/sync.md) |
| `status` | [Report project status in read-only mode](commands/status.md) |
| `review` | [Request an independent review](commands/review.md) |
| `refactor` | [Audit a project against its architecture and plan the refactoring](commands/refactor.md) |

For a bare invocation, a natural-language request without a command, or automatic selection, continue with the standard workflow below. A command word elsewhere in a request does not select a workflow. If the user clearly tries an unsupported command, show the five available commands before taking action.

## Choose the role and mode

| Request | Role |
| --- | --- |
| Define the product scope, write the PRD, refine or prioritize tickets | Product Owner (PO) |
| Define the architecture, the technology stack and code conventions, or evaluate a significant technical decision | Architect |
| Explicitly engage a Designer | Designer |
| Implement one or more identified tickets | Developer |
| Review a change independently of its author | Reviewer |
| Verify acceptance criteria and check for regressions | QA |

Read the relevant section of [roles.md](references/roles.md), then the context files that apply. If a request is ambiguous, start with a discussion or proposal. Interactive mode is the default. Take on the requested role in the conversation and distinguish between discussing, proposing, and editing.

The PO orchestrates delegated assignments, triages reports, and brings decisions and validations that require human input to the user. Direct interactive work in any requested role remains available.

Delegated mode requires an explicit request to delegate the assignment and an available, authorized native tool. Prepare each assignment using [missions.md](references/missions.md). Discovering the skill, finding a ready ticket, or completing an assignment never triggers a launch. Delegated agents do not delegate in turn. If the tool is unavailable, offer an assignment brief the user can pass to a separate session, or continue interactively if the role allows it. A self-review counts as a Developer check.

## Recover project context

Identify the project root and, before making any changes, the authoritative copy of the project. Resolve document paths using [documents.md](references/documents.md); paths in this skill and its resources are defaults for new projects, not a requirement to relocate existing documents. Read the PRD and the relevant sections of the backlog, architecture, ADRs, and any existing design documentation as needed for the assignment. Use the code and its tests to verify actual behavior. If sources disagree, raise the discrepancy with the relevant role before making a decision that depends on it.

| Project file | Rule |
| --- | --- |
| `docs/PRD.md` | Stable product foundation. For a new project, the PO defines it with the user and creates it first. Substantive revisions require an explicit decision from the user. |
| `docs/ARCHITECTURE.md` | The Architect creates it after the PRD. It defines the components, the technology stack, and the code organization and conventions. Architecture changes are based on an accepted ADR. |
| `docs/adrs/ADR_XXX.md` | One significant decision per file. The architecture document cites applicable ADRs. |
| `docs/BACKLOG.md` | Summary table followed by active phases, epics, and tickets. All backlog edits follow [backlog.md](references/backlog.md). |
| `docs/BACKLOG_ARCHIVE.md` | Full history of completed and cancelled tickets; their statuses remain distinct. Read only the entries needed for the assignment. |
| `docs/DESIGN.md` | Optional. Create or revise it when the user explicitly engages the Designer and asks to update the design guidelines. |

For an existing project, keep its current documents and identifiers. Flag gaps that prevent the assignment from proceeding and reuse reliable information. A diff review or a one-off check can start with the context available. The order for creating the PRD and architecture document applies only to initialization.

Use the [PRD](templates/PRD.md), [architecture](templates/ARCHITECTURE.md), [ADR](templates/ADR_XXX.md), [backlog](templates/BACKLOG.md), [archive](templates/BACKLOG_ARCHIVE.md), and [design](templates/DESIGN.md) templates when creating a document. Create the archive alongside a new backlog. Record decisions and progress needed to resume work in these files. Agents, assignment briefs, and interim reports are temporary. Record lasting facts in the relevant document or, through the authorized session, in the ticket.

## Protect parallel work

The PO can refine future tickets while Developers work on reserved tickets. Keep write scopes and the revisions under review separate. Every delegated agent treats the resolved Frame governance documents as read-only and submits proposed changes to them. Other documentation, including technical guides under `docs/`, may be edited within the explicit assignment scope. See the protected document list in [documents.md](references/documents.md). Only one authorized session writes to the authoritative copy of the backlog. If the writer's identity or the freshness of the copy is unclear, return a proposal for each ticket.

At the end of an assignment, report the work done, the evidence, the limitations, and any proposed updates. Distinguish agents actually launched, briefs ready to hand off, and results actually received. Parallel execution and the ability to continue the conversation during an assignment depend on the host. End assignments and release agents through the available mechanism.
