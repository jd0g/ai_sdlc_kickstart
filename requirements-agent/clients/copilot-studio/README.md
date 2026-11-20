# Copilot Studio Adapter

Use Copilot Studio as a team-facing agent surface while keeping requirements-engineering logic in the canonical repository.

Intended intents:
- Create User Needs
- Create/refine PRDs
- Decompose requirements
- Review requirements
- Check traceability and coverage
- Propose ADO changes

Map these intents to the canonical workflows in `../../skills/` and standards in `../../standards/`. Default to read/analyze/propose behavior. Controlled ADO writes require explicit human confirmation and post-write read-back.

If Copilot Studio requires consolidated instructions or knowledge artifacts, generate them through `../../build/` instead of manually maintaining separate rules.
