# Client Adapters

Cursor, GitHub Copilot, and Copilot Studio are client surfaces over one governed requirements-engineering core.

Client adapters contain only client-specific configuration and integration guidance. They must not redefine ISO 29148/EARS rules, traceability policy, ADO mappings, schemas, or workflow semantics.

Canonical sources remain:
- `../standards/`
- `../skills/`
- `../schemas/`
- `../evaluations/`

When a client requires self-contained instructions, create them from canonical sources in the build process. Do not maintain a second editable copy.
