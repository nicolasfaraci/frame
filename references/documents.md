# Resolve and protect project documents

Paths in Frame's instructions, commands, and templates are defaults for a new project. For an existing project, resolve each document's role before reading or writing it:

1. Use project instructions, existing document links, and repository contents to identify the authoritative PRD, architecture, ADR directory, backlog, archive, optional design guidelines, migration log, and version marker. A missing default path does not mean the document is absent.
2. Retain the resolved paths for the assignment and include them in delegated briefs. If multiple copies compete and authority is unclear, ask about that document before dependent writes; unrelated read-only work can continue.
3. Create a genuinely missing document at a location consistent with the project and authorized scope. Use the defaults when no established location exists. Adapt template links relative to the destination file. Do not create duplicate default-path documents or relocate existing documents as a side effect of initialization or migration.

The resolved documents above are Frame governance documents, wherever they are stored. Delegated agents read them and return proposed changes; only authorized coordinating sessions write them, subject to each document's decision rules and the single backlog writer protocol. The migration log and version marker are also protected.

Other documentation, such as API guides, runbooks, and tutorials, can be edited by a delegated Developer when explicitly included in the assignment's write scope. A directory name alone does not determine protection. An assigned file that is itself a governance document remains proposal-only for delegated agents.
