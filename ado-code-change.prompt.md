---
mode: agent
description: Structured implementation planning and execution for Azure DevOps code-change work items
---

## CONTEXT

You are working on a code-change work item originating from Azure DevOps.

The Azure DevOps MCP context may include:
- Title
- Description
- Acceptance Criteria
- Comments
- Attachments
- Linked work items
- Tags/Priority
- Definition of Done

If MCP context is incomplete, explicitly identify missing details.

---

## TECHNOLOGY CONTEXT

Determine the technology stack using:

1. Repository structure
2. Build/config files
3. Dependencies
4. Naming conventions
5. Existing patterns

If unclear, ask the user to confirm stack.

User override allowed:

STACK_OVERRIDE:
{{optional_stack}}

---

## OBJECTIVE

Convert the Azure DevOps work item into a safe, minimal, and verifiable code implementation plan aligned with repository conventions.

---

## STEP 1 — REQUIREMENT NORMALIZATION

Extract and output:

### Problem Statement
What behavior must change.

### Non-Goals
What must NOT change.

### Assumptions
Explicit + inferred assumptions.

### Acceptance Criteria (Normalized)
Rewrite ACs as precise technical expectations.

### Missing/Conflicting Info
Questions blocking implementation.

---

## STEP 2 — IMPACT ANALYSIS

Identify:

### Affected Layers
(e.g., API, domain logic, persistence, UI, integrations, infra)

### Affected Components
List files/modules/classes likely impacted.

### External Contracts
APIs, DB schema, message formats, events.

### Cross-Cutting Concerns
Auth, caching, logging, telemetry, validation, transactions.

### Backward Compatibility Risk
Explicit yes/no + explanation.

---

## STEP 3 — DESIGN OPTIONS

Provide 2–3 viable approaches:

For each:

- Description
- Required Changes
- Complexity
- Risk Level
- Test Impact
- Performance Impact
- Why it fits repo patterns

Recommend ONE option with reasoning.

---

## STEP 4 — IMPLEMENTATION PLAN

Produce atomic steps:

Each step must include:

- Goal
- Files impacted
- Type of change
- Dependencies
- Verification method

Steps must:

- Avoid large diffs
- Preserve public APIs unless required
- Follow repo conventions
- Avoid unnecessary abstractions

---

## STEP 5 — TEST STRATEGY

Map acceptance criteria → tests:

### Unit Tests
### Integration Tests
### Edge Cases
### Negative Cases
### Regression Coverage

Also list:

- Required test data
- Mocking/stubbing needs
- Observability checks

---

## STEP 6 — RISK ANALYSIS

List:

- Functional risks
- Performance risks
- Security risks
- Data integrity risks
- Deployment risks

Include mitigation for each.

---

## STEP 7 — ROLLOUT PLAN

If applicable:

- Feature flags
- Migration steps
- Backfill needs
- Monitoring signals
- Rollback approach

---

## STEP 8 — DONE CRITERIA

Define:

Checklist that must be true before PR merge.

---

## STEP 9 — PR OUTPUT

Generate:

### PR Title
### PR Description
- What
- Why
- How
- Tests
- Risks
- Rollout

---

## CONSTRAINTS

You MUST:

- Prefer minimal safe changes
- Follow existing architecture
- Avoid rewriting unrelated code
- Ask when unclear
- Avoid inventing patterns not present in repo
- Not assume unspecified business rules
- Be deterministic and structured

---

## OUTPUT DELIVERY MODE

Do NOT place the full response in chat.

Instead:

1. Generate markdown file(s) under:

docs/ado-workitems/{{workitem-id}}/

If workitem id unavailable, use timestamp.

2. Create files:

- summary.md → executive summary
- requirements.md → normalized requirements
- impact-analysis.md
- design-options.md
- implementation-plan.md
- test-strategy.md
- risks.md
- rollout-plan.md
- pr-draft.md

3. Chat output must contain ONLY:

- Short summary (max 8 bullets)
- List of created files
- Suggested next step

4. Keep files concise but complete.

5. Overwrite only if user confirms.

## STRICT CONSIDERATION
No fluff.
No repetition.
No generic advice.
Concrete repo-aware reasoning only.
