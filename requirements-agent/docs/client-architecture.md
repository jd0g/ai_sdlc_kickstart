# Client-Independent Architecture

## Principle
Cursor, GitHub Copilot, and Copilot Studio are interchangeable client surfaces over one governed requirements-engineering core.

## Core
- `standards/`: ISO 29148-aligned authoring, EARS, traceability/change control, and ADO mapping
- `skills/`: specialized requirements workflows
- `schemas/`: structured output contracts
- `evaluations/`: regression and quality evaluation suite

## Client adapters
- `clients/cursor/`
- `clients/github-copilot/`
- `clients/copilot-studio/`

## Systems of record
Git stores governed agent definitions and standards. Azure DevOps work items remain authoritative for controlled User Needs, requirements, trace links, verification, and lifecycle state.

## Integration boundary
Azure DevOps MCP or another approved tool layer supplies reads and approved writes. Client adapters must not bypass the human-in-the-loop controls in `standards/traceability.md`.
