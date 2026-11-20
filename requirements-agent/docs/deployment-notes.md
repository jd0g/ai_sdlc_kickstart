# Deployment Notes

## Cursor
Keep the complete repository in the workspace so each skill can resolve `../../standards/*.md`. Complete `standards/ado-mapping.md` with actual work-item types, fields, states, and links.

## Packaging trade-off
Standalone skill ZIPs generally contain only their own folder, so repository-level references will not travel with an individually packaged skill. For a self-contained runtime, use a build pipeline to inject read-only copies of canonical standards during packaging. The repository-level files remain authoritative; injected copies are generated artifacts.

## CI checks
Validate each SKILL.md; verify all standard references; reject hand-copied standards in source skill folders; run evaluation scenarios; and prevent any autonomous ADO approval or baseline action.
