---
name: create-prd
description: "Create or refine a PRD from user needs, product context, use cases, risks, architecture constraints, documents, and Azure DevOps items."
---
# Create PRD

## Canonical standards
Before executing this skill, read and apply:
- `../../standards/requirements-authoring.md`
- `../../standards/ears.md`
- `../../standards/traceability.md`
- `../../standards/ado-mapping.md`

If any file is unavailable, stop and report that the canonical standards could not be loaded. Do not substitute remembered or copied rules.

## Workflow
1. Establish purpose, users, problem, value, sources, scope, and exclusions.
2. Organize capabilities around outcomes and use cases.
3. Convert approved needs into product-level EARS requirements.
4. Cover nominal, alternate, exception, security, privacy, data, interface, operational, and failure scenarios as applicable.
5. Record constraints, assumptions, dependencies, risks, decisions, and unresolved questions.
6. Trace source → need → capability/use case → product requirement → verification.
7. Check duplicates, contradictions, hidden design choices, unsupported claims, and missing verification.
8. Present a review draft and ADO change plan; do not baseline or write without approval.

## Required sections
Document control; executive summary; problem/opportunity; stakeholders; goals/outcomes; scope/exclusions; boundaries; assumptions/constraints/dependencies; use cases; product requirements; data/interface/security/privacy/compliance/operations; verification; risks; traceability; open decisions; ADO change plan.

For each normative requirement include temporary ID, title, EARS statement, type, parent/source, rationale, verification method, acceptance evidence, supported priority/risk, and TBDs.
