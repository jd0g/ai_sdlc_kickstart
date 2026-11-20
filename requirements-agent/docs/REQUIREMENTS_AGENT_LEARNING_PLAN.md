# Requirements Agent Learning and Implementation Plan

**Owner:** Jason Kehl  
**Repository:** `requirements-agent`  
**Status:** Active  
**Last updated:** 2026-11-19  
**Target duration:** 12 weeks at approximately 4-6 hours per week

---

## 1. Purpose

This document provides:

1. A structured learning plan for designing and implementing a reusable agentic requirements-engineering system.
2. A progress tracker for the repository owner and team.
3. The original architectural context needed by a new AI session or contributor.
4. Concrete deliverables and completion criteria for each learning stage.

The intended system will help the team create and manage:

- User Needs
- Product Requirements Documents (PRDs)
- Product and system requirements
- Low-Level Requirements (LLRs)
- Traceability relationships
- Requirement reviews and quality findings
- Verification and test relationships
- Change-impact analysis

The team stores controlled requirements in Azure DevOps and frequently uses Cursor and Microsoft/GitHub Copilot for assisted engineering work. The solution must be reusable across the team so results do not depend primarily on an individual's prompt-writing ability or preferred AI client.

---

## 2. Original Context for New AI Sessions

Use the following context when beginning a new AI session about this repository:

> We are building a reusable, governed requirements-engineering system for a team that stores requirements in Azure DevOps. The system must support User Needs, PRDs, product/system requirements, Low-Level Requirements, traceability, requirement review, verification planning, and change-impact analysis. It must apply ISO/IEC/IEEE 29148-aligned quality characteristics and EARS requirement patterns. Azure DevOps is the controlled system of record. Git stores the standards, skills, schemas, evaluations, client adapters, and deployment assets. Cursor, GitHub Copilot, and Copilot Studio are client surfaces over the same governed core. The agent may analyze, draft, review, and propose changes, but controlled Azure DevOps writes require explicit human approval and post-write read-back verification. Do not create client-specific copies of the requirements standards. Generate deployable copies from canonical source when a client requires self-contained instructions.

### Architectural principles

- **Azure DevOps Boards is authoritative** for controlled User Needs, requirements, links, verification, and lifecycle state.
- **Git is authoritative** for agent standards, skills, structured schemas, evaluations, and deployment configuration.
- **The requirements logic is client-independent.** Cursor, GitHub Copilot, and Copilot Studio are interchangeable entry points where technically feasible.
- **Canonical standards are maintained once** under `standards/`.
- **Specialized skills are preferred over one large agent.**
- **Agent workflows combine reasoning with deterministic operations.** ADO write operations should be deterministic and approval-gated.
- **Structured outputs are preferred over prose-only outputs.**
- **The authoring agent must not approve its own output.**
- **Evaluation is required before team-wide deployment.**

### Intended repository structure

```text
requirements-agent/
├── README.md
├── standards/
│   ├── requirements-authoring.md
│   ├── ears.md
│   ├── traceability.md
│   └── ado-mapping.md
├── skills/
│   ├── create-user-needs/
│   ├── create-prd/
│   ├── decompose-requirements/
│   └── review-requirements/
├── schemas/
├── evaluations/
├── clients/
│   ├── cursor/
│   ├── github-copilot/
│   └── copilot-studio/
├── build/
└── docs/
```

### Initial specialized skills

1. `create-user-needs`
2. `create-prd`
3. `decompose-requirements`
4. `review-requirements`

Potential later skills:

- `check-traceability`
- `analyze-change-impact`
- `generate-verification-scenarios`
- `detect-duplicate-requirements`
- `prepare-requirements-baseline`

---

## 3. Target Architecture

```text
                         USERS
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
      Cursor       GitHub Copilot     Copilot Studio
        │                  │                  │
        └──────────────────┼──────────────────┘
                           │
                  Requirements Skills
                           │
          ┌────────────────┼────────────────┐
          │                │                │
   User Need Agent      PRD Agent    Decomposition Agent
          │                │                │
          └────────────────┼────────────────┘
                           │
                  Requirements Critic
                           │
                  Traceability Checking
                           │
                    Human Approval
                           │
                 Azure DevOps MCP/Tools
                           │
                    Azure DevOps
                   System of Record
```

The core is not a chatbot. It is a controlled requirements-engineering workflow supported by specialized AI reasoning and deterministic integration tools.

---

## 4. Learning Objectives

By completing this plan, the owner should be able to:

- Apply ISO/IEC/IEEE 29148 principles to User Needs and requirements.
- Write and review requirements using EARS patterns.
- Design schemas for structured LLM output.
- Design MCP tools and safe Azure DevOps read/write workflows.
- Separate agentic reasoning from deterministic workflow operations.
- Build reusable skills that produce consistent team results.
- Establish human approval boundaries for controlled requirements.
- Create an evaluation harness and regression dataset.
- Implement traceability and change-impact analysis.
- Expose one governed requirements capability through multiple AI clients.

---

## 5. Recommended Learning Order

1. Requirements engineering and EARS
2. Structured LLM outputs and schema design
3. Azure DevOps data model and MCP/tool architecture
4. Reusable client-independent skills
5. Agentic review and human approval controls
6. Evaluation and regression testing
7. Requirement-to-test integration
8. Change-impact analysis
9. Team deployment and governance

Do not begin with a multi-agent orchestration framework. The central problem is reproducible engineering behavior, controlled context, traceability, validation, and safe ADO changes, not getting multiple agents to converse.

---

# 6. Twelve-Week Learning and Build Plan

## Stage 1: Requirements Engineering Foundation

**Timing:** Weeks 1-2  
**Primary topics:** ISO/IEC/IEEE 29148, EARS, hierarchy, traceability, verification

### Learn

- ISO/IEC/IEEE 29148 requirement quality characteristics:
  - necessary
  - appropriate
  - unambiguous
  - complete
  - singular
  - feasible
  - verifiable
  - correct
  - conforming
  - traceable
- User Need → Product/System Requirement → Low-Level Requirement decomposition.
- EARS patterns:
  - ubiquitous
  - event-driven
  - state-driven
  - optional feature
  - unwanted behavior
  - complex
- Verification methods:
  - inspection
  - analysis
  - demonstration
  - test
- Derived requirements, assumptions, constraints, and rationale.
- Gherkin/BDD as a downstream verification technique.
- SysML and MBSE concepts at an overview level.

### Build

- Review and refine:
  - `standards/requirements-authoring.md`
  - `standards/ears.md`
  - `standards/traceability.md`
- Add at least 10 approved examples and 10 defective examples.
- Document the team's artifact hierarchy and terminology.

### Completion criteria

- [ ] I can distinguish a User Need from a system requirement and an LLR.
- [ ] I can identify the applicable EARS pattern for a requirement.
- [ ] I can explain why a requirement is or is not independently verifiable.
- [ ] I can identify compound, vague, implementation-biased, and untraceable requirements.
- [ ] Canonical standards have been reviewed by at least one systems, quality, or requirements stakeholder.

### Evidence

- Link to pull request:
- Reviewer:
- Date completed:
- Notes:

---

## Stage 2: Structured AI Outputs

**Timing:** Weeks 3-4  
**Primary topics:** JSON Schema, structured output, context engineering, prompt composition

### Learn

- JSON Schema fundamentals.
- Required vs optional fields.
- Enumerations and controlled vocabularies.
- Identifier strategies for candidate and committed items.
- Structured LLM output and schema validation.
- Separation between reasoning representation and ADO field representation.
- Context selection and retrieval boundaries.

### Build

Create schemas for:

- `schemas/user-need.schema.json`
- `schemas/prd.schema.json`
- `schemas/requirement.schema.json`
- `schemas/review-finding.schema.json`
- `schemas/trace-link.schema.json`
- `schemas/ado-change-plan.schema.json`

Minimum requirement fields should include:

```text
candidate_id
committed_ado_id
artifact_type
title
statement
rationale
source_ids
parent_id
allocation
verification_method
acceptance_evidence
priority
risk_ids
assumptions
tbd_items
open_questions
confidence
```

### Completion criteria

- [ ] Every skill has a defined structured output contract.
- [ ] Candidate IDs are clearly separated from committed ADO IDs.
- [ ] Invalid output fails validation rather than being silently accepted.
- [ ] Missing authoritative values are represented as TBD or open questions.
- [ ] The schema does not hard-code client-specific fields.

### Evidence

- Link to pull request:
- Schema validation command:
- Date completed:
- Notes:

---

## Stage 3: Azure DevOps and MCP Integration

**Timing:** Weeks 5-6  
**Primary topics:** ADO work items, fields, links, queries, revision control, MCP tools

### Learn

- ADO process templates and custom work-item types.
- Work-item fields and reference names.
- Parent/child and related-link semantics.
- Requirement-to-test relationships.
- WIQL and saved queries.
- ADO revision numbers and optimistic concurrency.
- MCP tool definitions and least-privilege tool exposure.
- Idempotency, retries, read-back verification, and error handling.

### Build

Complete `standards/ado-mapping.md` with actual values for:

- User Need work-item type
- Product/System Requirement work-item type
- LLR work-item type
- controlled statement field
- rationale and source fields
- verification method field
- priority and risk fields
- workflow states
- parent/child link type
- requirement-to-test link type
- duplicate/superseded link type

Define the minimum MCP/tool operations:

```text
get_work_item
get_work_items_batch
search_requirements
run_requirement_query
get_parent_and_children
get_links
create_work_item
update_work_item
create_child
link_work_items
get_test_cases
create_or_link_test_case
read_back_changed_items
```

### Safety requirements

- Read before update.
- Present a change plan before write.
- Obtain explicit human confirmation.
- Use optimistic concurrency when supported.
- Read back changed records.
- Never claim success without tool evidence.
- Never automatically approve, baseline, or delete controlled requirements.

### Completion criteria

- [ ] `ado-mapping.md` reflects the real ADO configuration.
- [ ] All ADO fields and link types have been verified rather than guessed.
- [ ] Read-only workflows work before write tools are introduced.
- [ ] Controlled writes are confirmation-gated.
- [ ] Post-write read-back is implemented.
- [ ] Failed or partial writes produce a clear recovery path.

### Evidence

- ADO test project:
- Test work-item IDs:
- Link to tool definitions:
- Date completed:
- Notes:

---

## Stage 4: Reusable Client-Independent Skills

**Timing:** Week 7  
**Primary topics:** Skill design, consistent workflows, client adapters

### Learn

- Skill triggering descriptions.
- Progressive disclosure of standards and references.
- Workflow decomposition.
- Clear inputs, outputs, stop conditions, and guardrails.
- Client adapter design.

### Build

Complete and validate:

- `skills/create-user-needs/`
- `skills/create-prd/`
- `skills/decompose-requirements/`
- `skills/review-requirements/`

Ensure each skill:

- loads canonical standards;
- defines required inputs;
- separates sourced facts from assumptions;
- defines structured outputs;
- stops rather than inventing consequential information;
- produces an ADO change plan;
- requires confirmation before controlled writes;
- is usable by Cursor and GitHub Copilot;
- has a documented Copilot Studio adaptation path.

### Completion criteria

- [ ] No skill contains a separately maintained copy of ISO 29148/EARS rules.
- [ ] Each skill has clear trigger conditions and exclusions.
- [ ] Each skill has stop conditions for missing authoritative data.
- [ ] The same sample input produces materially comparable output across supported clients.
- [ ] Client configuration changes presentation/integration, not requirement semantics.

### Evidence

- Skill validation results:
- Cross-client comparison:
- Date completed:
- Notes:

---

## Stage 5: Agentic Review and Human-in-the-Loop Controls

**Timing:** Week 8  
**Primary topics:** author/critic separation, approval gates, controlled state transitions

### Learn

- Agent vs deterministic workflow boundary.
- Author-critic patterns.
- Self-review limitations.
- Approval gates and disposition records.
- Safe handling of approved or baselined items.

### Build

Implement the logical workflow:

```text
Source/Input
   ↓
Authoring Skill
   ↓
Requirements Review Skill
   ↓
Traceability Check
   ↓
Proposed Change Plan
   ↓
Human Approval
   ↓
ADO Writer
   ↓
Read-Back Verification
```

Recommended lifecycle states:

```text
DRAFT → AI REVIEWED → HUMAN REVIEWED → APPROVED
```

Map these to actual ADO states only after confirming the configured process.

### Completion criteria

- [ ] The authoring workflow cannot approve its own results.
- [ ] Findings include Blocker, Major, Minor, and Advisory severity.
- [ ] Proposed changes show creates, updates, links, and unchanged items.
- [ ] Human confirmation is explicit and scoped to the proposed change set.
- [ ] Approved/baselined requirements receive additional protection.

### Evidence

- Demonstration scenario:
- Reviewer:
- Date completed:
- Notes:

---

## Stage 6: Evaluation Harness

**Timing:** Weeks 9-10  
**Primary topics:** gold datasets, regression testing, measurable quality

### Learn

- Evaluation dataset design.
- Human-approved gold results.
- Deterministic vs model-judged metrics.
- Prompt/skill regression testing.
- Cross-client and cross-model comparison.

### Build

Create 20-50 representative scenarios covering:

- clear User Need inputs;
- incomplete or ambiguous source material;
- compound requirements;
- duplicate and contradictory requirements;
- incorrect abstraction levels;
- missing verification evidence;
- missing traceability;
- valid and invalid EARS patterns;
- unauthorized write attempts;
- partial ADO tool failures.

Initial release targets:

| Metric | Target |
|---|---:|
| Schema validity | 100% |
| Correct parent/child trace | 100% |
| Autonomous approval/baseline actions | 0 |
| Invented mandatory thresholds | 0 |
| Requirement atomicity | ≥95% |
| Verifiability | ≥95% |
| Traceability completeness | 100% for release set |
| Duplicate requirements introduced | <2% |
| Correct hierarchy/allocation | 100% for release set |

### Completion criteria

- [ ] Evaluation cases are version-controlled.
- [ ] Expected outputs are human-approved.
- [ ] Every change to standards or skills runs the evaluation suite.
- [ ] Failures identify the affected skill and quality criterion.
- [ ] Release criteria are defined and enforced.

### Evidence

- Evaluation report:
- Baseline version/tag:
- Date completed:
- Notes:

---

## Stage 7: Verification and Test Integration

**Timing:** Week 11  
**Primary topics:** requirement-to-test flow, acceptance evidence, objective evidence

### Learn

- Requirement verification planning.
- Gherkin/BDD scenario construction.
- ADO Test Plans relationships.
- Manual vs automated test traceability.
- Objective evidence and release trace.

### Build

Support this lifecycle:

```text
Business Need
  ↓
User Need
  ↓
PRD / Use Case
  ↓
Product Requirement
  ↓
Low-Level Requirement
  ↓
Design / Implementation
  ↓
Test Scenario
  ↓
Test Case
  ↓
Objective Evidence
```

Add or plan the `generate-verification-scenarios` skill. Ensure generated test scenarios trace to specific requirements and do not create unsupported behavior.

### Completion criteria

- [ ] Every requirement has a planned verification method.
- [ ] Test scenarios trace to requirement IDs.
- [ ] Acceptance evidence is objective and observable.
- [ ] The system distinguishes requirement defects from test defects.
- [ ] Test creation follows the same human approval boundary.

### Evidence

- Requirement IDs:
- Related test case IDs:
- Date completed:
- Notes:

---

## Stage 8: Change-Impact Analysis and Team Deployment

**Timing:** Week 12 and subsequent iterations  
**Primary topics:** impact graph, production governance, adoption

### Learn

- Graph-based traceability concepts.
- Change propagation.
- Configuration/baseline management.
- Deployment governance.
- Monitoring and feedback.

### Build

Design `analyze-change-impact` to report:

```text
Changed requirement
Affected upstream User Needs
Affected child and related requirements
Affected designs/components
Affected code/configuration
Affected risks and controls
Affected tests
Affected released baselines
Recommended regression scope
Unresolved impact questions
```

Deploy progressively:

1. Personal read-only use.
2. Small pilot with architects/requirements engineers.
3. Proposal-only ADO integration.
4. Approval-gated writes in a test project.
5. Approval-gated writes in the production project.
6. Team-facing Copilot Studio experience when governance and evaluation gates are met.

### Completion criteria

- [ ] Impact analysis follows both upstream and downstream links.
- [ ] Missing trace links are reported as uncertainty, not assumed to mean no impact.
- [ ] Pilot users complete defined scenarios successfully.
- [ ] Audit and support ownership are assigned.
- [ ] Versioning, rollback, and incident handling are documented.
- [ ] Team training and onboarding materials are available.

### Evidence

- Pilot participants:
- Release tag:
- Production approval:
- Date completed:
- Notes:

---

# 7. Progress Dashboard

| Stage | Status | Target date | Completion date | Evidence/PR |
|---|---|---|---|---|
| 1. Requirements engineering | Not started | | | |
| 2. Structured AI outputs | Not started | | | |
| 3. ADO and MCP integration | Not started | | | |
| 4. Reusable skills | In progress | | | |
| 5. Agentic review and approvals | Not started | | | |
| 6. Evaluation harness | Not started | | | |
| 7. Verification/test integration | Not started | | | |
| 8. Change impact and deployment | Not started | | | |

Allowed status values:

```text
Not started
In progress
Blocked
Ready for review
Complete
```

---

# 8. Decision Log

| Date | Decision | Rationale | Owner | Related PR/Issue |
|---|---|---|---|---|
| 2026-11-19 | Use Azure DevOps as the controlled system of record | Requirements, links, lifecycle state, and tests need controlled enterprise storage | Jason Kehl | |
| 2026-11-19 | Keep standards and skills in Git | Enables versioning, review, reuse, and regression evaluation | Jason Kehl | |
| 2026-11-19 | Use client-independent core with thin adapters | Avoid dependence on Cursor, GitHub Copilot, or Copilot Studio | Jason Kehl | |
| 2026-11-19 | Centralize ISO 29148/EARS standards | Prevent inconsistent copies across skills and clients | Jason Kehl | |
| 2026-11-19 | Require explicit human approval for ADO writes | Protect controlled requirements and preserve accountability | Jason Kehl | |

---

# 9. Risks and Mitigations

| Risk | Consequence | Mitigation |
|---|---|---|
| Skills drift from canonical standards | Inconsistent requirements across users | Reference canonical files; generate copies only during build |
| Agent invents missing details | Invalid or unsafe controlled requirements | Use TBD/open questions; implement stop conditions and evaluations |
| Duplicate requirements are created | Conflicting implementation and testing | Search existing ADO items and sibling requirements before proposing creates |
| Agent overwrites concurrent ADO changes | Lost updates | Read before write; use revision checks/optimistic concurrency |
| Authoring agent approves its own output | Weak independent review | Separate author, critic, and human approval roles |
| Client behavior differs materially | Team receives inconsistent results | Cross-client evaluations using the same scenarios |
| Copilot Studio cannot resolve repo-relative references | Deployment diverges from source | Generate a deployment bundle from canonical source during CI/build |
| Traceability is incomplete | Change-impact analysis produces false confidence | Report missing links as uncertainty and make trace completeness a release gate |
| Framework complexity grows too early | Slow delivery and difficult maintenance | Prefer specialized skills and deterministic workflows before orchestration frameworks |

---

# 10. Definition of Done for the Initial Release

The initial release is ready for a limited team pilot when:

- [ ] Canonical requirements, EARS, traceability, and ADO mapping standards are approved.
- [ ] Four initial skills are complete and validated.
- [ ] Structured output schemas exist and enforce required fields.
- [ ] At least 20 representative evaluation cases pass release thresholds.
- [ ] Read-only ADO retrieval works reliably.
- [ ] Proposal-only workflows work without modifying ADO.
- [ ] Approval-gated ADO writes have been tested in a non-production project.
- [ ] Post-write read-back verification works.
- [ ] The author cannot approve its own output.
- [ ] Audit, support, versioning, rollback, and ownership are documented.
- [ ] Cursor and GitHub Copilot produce materially comparable results for the pilot scenarios.
- [ ] The Copilot Studio deployment approach is documented, even if it is not part of the first pilot.

---

# 11. Recommended Personal Focus

As Principal Data Architect and system owner, prioritize:

1. Requirements engineering and EARS
2. Structured output and schema design
3. MCP/tool architecture
4. Agent/workflow architecture
5. LLM evaluation and governance

Framework-specific implementation can be distributed to developers. The highest-leverage responsibility is defining a system in which multiple team members and AI clients produce comparable, traceable, reviewable, and safe engineering artifacts.

---

# 12. AI Session Start Prompt

Paste or reference this section when starting a new AI session:

> Work from the `requirements-agent` repository. Begin by reading this learning plan, the root README, all files under `standards/`, and the applicable `skills/<skill-name>/SKILL.md`. Treat Azure DevOps as the controlled system of record and Git as the source of truth for standards, skills, schemas, evaluations, and client adapters. Apply ISO/IEC/IEEE 29148-aligned quality characteristics and the EARS patterns defined in the repository. Separate sourced facts from assumptions and never invent thresholds, IDs, fields, risks, interfaces, or regulatory classifications. Use TBD and targeted questions for missing authoritative values. Before any ADO write, read current state, show a proposed change plan, obtain explicit approval, commit only the approved scope, and read the result back. Never autonomously approve, baseline, delete, or silently modify controlled requirements. Keep the solution client-independent unless the task explicitly concerns a client adapter.

---

# 13. Next Actions

- [ ] Add this file to the repository as `docs/REQUIREMENTS_AGENT_LEARNING_PLAN.md`.
- [ ] Complete the actual values in `standards/ado-mapping.md`.
- [ ] Add JSON Schemas under `schemas/`.
- [ ] Add 10 good and 10 defective requirement examples.
- [ ] Create the first evaluation cases under `evaluations/`.
- [ ] Select one real, low-risk User Need/requirement chain for the first end-to-end pilot.
