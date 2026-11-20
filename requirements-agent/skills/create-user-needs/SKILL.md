---
name: create-user-needs
description: "Create, refine, or normalize stakeholder-focused user needs from ideas, problems, interviews, business goals, risks, documents, or Azure DevOps context."
---
# Create User Needs

## Canonical standards
Before executing this skill, read and apply:
- `../../standards/requirements-authoring.md`
- `../../standards/ears.md`
- `../../standards/traceability.md`
- `../../standards/ado-mapping.md`

If any file is unavailable, stop and report that the canonical standards could not be loaded. Do not substitute remembered or copied rules.

## Workflow
1. Separate sourced facts, assumptions, constraints, risks, and open questions.
2. Identify the stakeholder and outcome without embedding a technical solution unless mandated.
3. Cluster overlaps and retain one outcome per need.
4. Draft using: `<actor> needs the ability to <outcome> [so that <value>]` or the approved convention.
5. Trace each need to its source; label inferred needs as Derived and explain why.
6. Check necessity, ambiguity, singularity, feasibility, and decomposability.
7. Compare with existing ADO items for duplicates and conflicts.
8. Present candidates and an ADO change plan. Write only after explicit approval.

## Output
For each candidate include temporary ID, title, statement, stakeholder, rationale/value, source trace, supported priority, Direct/Derived type, outcome-level success evidence, dependencies, and duplicate/conflict assessment. Include coverage gaps, assumptions, open questions, and proposed ADO fields/links.

## Guardrails
Do not turn user needs into design tasks, silently promote assumptions, or create redundant needs.
