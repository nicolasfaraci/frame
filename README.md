# Install Frame

1. Keep the entire `frame` folder together, including `commands/`, `references/`, and `templates/`.
2. Copy it to the location for your tool. The project paths are relative to the repository root.
3. Open the project in the tool. If the skill does not appear, open a new session or restart the tool.

| Tool | Project | Personal installation | Invocation |
| --- | --- | --- | --- |
| Codex | `.agents/skills/frame/` | `~/.agents/skills/frame/` | Select `$frame` in the prompt |
| Claude Code | `.claude/skills/frame/` | `~/.claude/skills/frame/` | Enter `/frame` followed by your request |

Check that `SKILL.md` is directly inside the copied `frame/` folder. [Installing in Codex](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) · [Installing in Claude Code](https://code.claude.com/docs/en/skills#choose-where-skills-load)

## Standard use

Invoke `$frame` or `/frame` with a normal request. The host can also select the skill automatically when the request matches its description. Try one of these requests.

- “Act as PO. Let's discuss the criteria for our upcoming tickets while T-041 is in progress. Keep new ideas as proposals.”
- “This session owns the authoritative backlog. Delegate T-042 and T-043 in parallel if both tickets are ready and can be isolated.”
- “Request an independent review of T-042 at the revision listed in the ticket.”

Delegated agents receive one-off assignments through the available native tools. If delegation is unavailable, the skill can prepare briefs to pass to separate sessions. Whether you can keep talking in the same session while work runs depends on the tool. If two sessions are working on the same project, designate the one that writes to the authoritative backlog. [Codex subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents) · [Claude Code subagents](https://code.claude.com/docs/en/sub-agents)

## Optional commands

| Codex | Claude Code | Result |
| --- | --- | --- |
| `$frame init` | `/frame init` | Initialize documentation or propose missing files in an existing project. |
| `$frame sync` | `/frame sync` | Inspect documentation and propose a migration for approval. |
| `$frame status` | `/frame status` | Summarize project progress and blockers without editing files. |
| `$frame review T-042` | `/frame review T-042` | Request an independent review of a ticket or change. |

## Project workflow

The PO coordinates temporary agents, reprioritizes Developer, Reviewer, and QA findings, and brings decisions requiring human input to the user. The authorized backlog writer keeps the summary at the top of `docs/BACKLOG.md` current and moves completed and cancelled tickets with their distinct statuses and history into `docs/BACKLOG_ARCHIVE.md`.

For an existing project, use `sync` to compare its documentation with the current Frame conventions, even if it has no version marker. Approved migrations are logged in `docs/FRAME-MIGRATIONS.md` and record the resulting documentation version in `docs/.frame-version`. [Migration notes](references/migrations.md)

Existing document paths are preserved. Only Frame governance documents are read-only for delegated agents; assigned technical guides can be edited. Independent review can run directly in a session that did not implement the change. Local changes are identified by reproducible snapshots when no commit captures the target.

## Validation

Use the [behavioral scenarios](tests/scenarios.md) to check role decisions, exact review targets, custom paths, cancellation, and recovery. Run evaluations in disposable projects and score resulting actions and artifacts rather than matching wording.
