# Development & Documentation Protocol

## Code Standards

- Code must be well-structured, modular, loosely coupled, and maintainable, enabling easy modification, extension, and handover.
- Workflows and data flows must be simple and efficient. Tests must be standardized, reproducible, and efficient, without redundant steps or compromised coverage.

## File Responsibilities & Update Triggers

Documentation must be concise, precise, and professional.

- `README.md`: Project overview, structure, setup, and documentation entry points. Update when project structure, dependencies, setup, or usage changes.
- `AGENTS.md`: Development standards, Agent instructions, and documentation rules. Update when development, testing, or collaboration requirements change.
- `Docs/`: Contains only four directories and `current.md`:
  - `kedb/`: Known Error Database. Known issues, triggers, root causes, fixes, and workarounds. Review before each development session ends; update when issues or findings change. Mark unconfirmed causes.
  - `runbooks/`: Verified procedures, prerequisites, and success criteria. Update when repeatable procedures are established or modified.
  - `playbooks/`: Diagnostic workflows, decision branches, remediation, and escalation paths. Update when reusable troubleshooting procedures are established or improved.
  - `postmortems/`: Major incident impact, timelines, root causes, and corrective actions. Update after incident reviews or corrective-action validation.
  - `current.md`: Current development and operational status, active tasks, blockers, and next steps. Update on significant status, phase, or risk changes, and before each development session ends. Exclude historical logs.
- `Knowledge/`: Architecture, technical decisions, interface contracts, core mechanisms, and long-term constraints. Update when significant technical knowledge or decisions change.
- `ArchiveDocs/`: Obsolete or superseded documentation. Archive when replaced by current implementations, designs, or procedures. Not authoritative for current operations.

## Documentation Format

Each topic in `Docs/`, `Knowledge/`, and `ArchiveDocs/` must have a separate Markdown file with a short, descriptive filename and YAML Front Matter:

```yaml
---
summary: One-line description of the topic and scope
tags: [module, keyword]
updated: "YYYY-MM-DD"
version: "1.0.0"
---
```

`version` is required and identifies the project version at which the document was last validated. Maintain versions consistently, manually or via Git tags.

Include relevant conditions, technical rationale, procedures, outcomes (including useful failures), and verification methods as needed. No fixed section structure is required.

## Documentation Access & Maintenance

- Search first: Use `rg -n 'error_code|keyword' Docs/ Knowledge/`. Consult `ArchiveDocs/` only for historical investigation.
- Update in place: Follow directory responsibilities. Prefer existing entries; create new files only for distinct, reusable knowledge. Use relative links instead of duplicating content.
- Update on change: Record relevant evidence, outcomes, and verification. Update `updated` accordingly. Avoid redundant logs.
- Archive obsolete content: Preserve valid constraints in current documentation before archiving. Retain incident records when needed for traceability.
- Synchronize changes: Keep documentation aligned with code. When using Git, commit related changes together; local commits are sufficient.

Core Principles: Clear Responsibilities, Search First, Event-Driven Updates, No Duplication, and Lifecycle Management.
