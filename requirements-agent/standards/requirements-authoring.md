# Requirements Authoring Standard

Azure DevOps is the authoritative record for controlled requirements. Agents may draft, analyze, and propose changes, but a person must approve controlled writes, baselines, and dispositions.

## ISO/IEC/IEEE 29148-aligned quality characteristics
Every requirement must be necessary, appropriate to its abstraction level, unambiguous, complete, singular, feasible, verifiable, correct, conforming, and traceable.

- Trace each statement to an approved need, risk control, constraint, interface obligation, or justified derivation.
- Use one subject and one primary obligation per requirement.
- State applicable triggers, conditions, behavior, objects, limits, tolerances, and failure responses.
- Keep implementation choices out unless an approved constraint mandates them.
- Define observable evidence using inspection, analysis, demonstration, or test.
- Preserve approved terminology, identifiers, units, and source intent.

## Normative language
- Use **shall** for product, system, subsystem, software, data, interface, security, and low-level requirements.
- Use **needs the ability to** or the approved team convention for user needs.
- Do not use should, may, could, aims to, or is intended to for mandatory behavior.
- Use **TBD** when an authoritative value is missing. Never invent thresholds, actors, interfaces, IDs, risks, or compliance classifications.

## Ambiguity check
Flag these terms unless objectively defined: appropriate, adequate, easy, efficient, fast, flexible, normally, quickly, reliable, robust, seamless, sufficient, timely, user-friendly, as needed, if possible, and etc.

## Minimum requirement record
ID, title, statement, type/allocation, upstream trace, rationale, verification method, acceptance evidence, supported priority/risk links, assumptions/TBDs, status, and owner when available.
