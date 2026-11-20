# Traceability and Change-Control Standard

## Minimum chain
Business objective/source → User Need → Product/System Requirement → Low-Level Requirement → Design/Implementation → Verification/Test → Objective Evidence.

- Every item needs authoritative upstream justification or an explicit derived-requirement rationale.
- Every approved parent needs sufficient downstream coverage or a documented disposition.
- Every requirement needs a verification method and identifiable acceptance evidence.
- Use one primary parent; use related links for valid secondary trace instead of duplication.
- Preserve stable IDs and record change rationale and downstream impact.
- Identify orphans, uncovered parents, broken test links, duplicates, conflicts, and inconsistent thresholds.

## ADO control boundary
Before a write: read current state, show proposed changes, obtain explicit approval, commit only approved changes, then read back and report actual IDs and links. Never autonomously approve, baseline, delete, or silently alter an approved requirement.
