# Requirements Agent Repository

Reusable requirements engineering workflows for Cursor and Azure DevOps.

- `standards/`: one canonical source for authoring, EARS, traceability, and ADO mapping
- `skills/`: Create User Needs, Create PRD, Decompose Requirements, Review Requirements
- `schemas/`: structured-output contracts
- `evaluations/`: regression scenarios and approved results
- `docs/`: deployment and governance guidance
- `clients/`: thin adapters for Cursor, GitHub Copilot, and Copilot Studio
- `build/`: generated deployment artifacts and packaging automation

Keep the full repository available to the agent because skills resolve shared standards through repository-relative paths. Govern standards through pull requests, evaluate changes, tag releases, and treat ADO as the authoritative controlled record.
