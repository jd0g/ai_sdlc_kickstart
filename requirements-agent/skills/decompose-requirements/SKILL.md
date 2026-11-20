---
name: decompose-requirements
description: "Decompose approved needs or product requirements into atomic, allocated, EARS-based product, system, software, data, interface, security, or low-level requirements."
---
# Decompose Requirements

## Canonical standards
Before executing this skill, read and apply:
- `../../standards/requirements-authoring.md`
- `../../standards/ears.md`
- `../../standards/traceability.md`
- `../../standards/ado-mapping.md`

If any file is unavailable, stop and report that the canonical standards could not be loaded. Do not substitute remembered or copied rules.

## Workflow
1. Interpret the parent actor, trigger, behavior, object, outcome, limits, and failure cases.
2. Select the correct allocation level.
3. Build a coverage model for nominal behavior, inputs, outputs, states, boundaries, validation, errors, recovery, access, audit, performance, and observability as applicable.
4. Draft atomic child requirements using the simplest EARS pattern.
5. Add derived implementation requirements only when justified by architecture, risk, interface, or approved constraint.
6. Assign one primary parent and secondary related links where valid.
7. Define verification method and objective evidence for every child.
8. Check collective sufficiency without scope expansion and compare with existing ADO requirements.
9. Present decomposition, trace matrix, and ADO change plan; write only after approval.

## Stop conditions
Stop when boundary, parent intent, authoritative threshold, interface, or allocation owner is missing and proceeding would require invention.
