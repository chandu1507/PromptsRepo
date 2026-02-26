---
mode: agent
description: Structured defect investigation, root cause analysis, and safe remediation planning for Azure DevOps work items
---

## CONTEXT

You are investigating a defect reported via Azure DevOps.

The MCP context may include:
- Title
- Description
- Reproduction steps
- Environment details
- Logs/screenshots
- Acceptance criteria
- Linked incidents
- Severity/Priority

If critical information is missing, explicitly identify it.

---

## TECHNOLOGY CONTEXT

Auto-detect technology stack from repository structure and patterns.

Optional override:

STACK_OVERRIDE:
{{optional_stack}}

---

## OBJECTIVE

Perform structured defect investigation before proposing any fix.

Do NOT jump to implementation.

---

# STEP 1 — DEFECT NORMALIZATION

Extract and restate:

### Observed Behavior
What actually happens.

### Expected Behavior
What should happen.

### Reproduction Steps
Rewrite clearly and deterministically.

### Environment Context
Dev/Test/Prod?
Data state?
Feature flags?
Dependencies?

### Severity Classification
Functional / Performance / Data / Security / UX / Intermittent.

### Missing Information
Explicit list of unknowns blocking investigation.

---

# STEP 2 — REPRODUCTION STRATEGY

Define:

- How to reproduce locally.
- Required data setup.
- Required configuration.
- Logging required to confirm behavior.
- Test case to codify reproduction.

If reproduction is not deterministic:
- Identify variables.
- Identify timing/race conditions.
- Identify external dependencies.

---

# STEP 3 — IMPACT ANALYSIS

Determine:

### Scope
Which modules/components likely involved.

### Surface Area
API, UI, DB, background jobs, integrations.

### Affected Users
Who is impacted.

### Regression Risk
Was this working before?
What recent changes may relate?

### Related Work Items
Search repo patterns for similar fixes.

---

# STEP 4 — ROOT CAUSE HYPOTHESIS

List 3–5 plausible root causes ranked by probability.

For each:

- Why it is plausible
- Code locations to inspect
- How to confirm or eliminate

Do not assume a single cause prematurely.

---

# STEP 5 — ROOT CAUSE CONFIRMATION PLAN

Define:

- Logs to add
- Breakpoints to place
- Data queries to run
- Unit/integration tests to create
- Edge cases to simulate

Goal: Confirm exact failing invariant.

---

# STEP 6 — FIX OPTIONS

After root cause identified, propose:

2–3 remediation approaches.

For each:

- Description
- Scope of change
- Risk level
- Backward compatibility impact
- Performance impact
- Complexity
- Test requirements

Recommend safest minimal fix.

---

# STEP 7 — SAFE IMPLEMENTATION PLAN

Produce atomic steps:

Each step includes:

- Files impacted
- What changes
- Why change is safe
- Verification method

Constraints:

- Minimal diff
- No architecture rewrite
- Preserve unrelated behavior
- Avoid introducing new abstractions

---

# STEP 8 — REGRESSION STRATEGY

Define:

### Characterization Tests
Lock current correct behavior.

### Regression Tests
Cover bug scenario.

### Boundary Tests
Edge cases around defect.

### Monitoring Signals
Logs/metrics to detect recurrence.

---

# STEP 9 — RISK ANALYSIS

List:

- Functional risks
- Data corruption risk
- Concurrency risk
- Performance risk
- Security implications
- Deployment risk

Mitigation for each.

---

# STEP 10 — ROLLOUT PLAN

Address:

- Safe deployment strategy
- Feature flag if needed
- Hotfix vs normal release
- Backfill data if applicable
- Rollback strategy

---

# STEP 11 — DONE CRITERIA

Checklist that must be true before merge.

---

# STEP 12 — PR OUTPUT

Generate:

### PR Title
### PR Description
- Summary of defect
- Root cause
- Fix approach
- Tests added
- Risks
- Rollout plan

---

# OUTPUT DELIVERY MODE

Do NOT place full output in chat.

Create markdown files under:

docs/ado-defects/{{workitem-id}}/

Files:

- summary.md
- reproduction.md
- impact-analysis.md
- root-cause.md
- remediation-options.md
- implementation-plan.md
- regression-tests.md
- risks.md
- rollout.md
- pr-draft.md

Chat must contain ONLY:

- 6–8 bullet executive summary
- List of files created
- Next recommended action

If work item ID unavailable, use timestamp.

---

# CONSTRAINTS

You MUST:

- Not jump directly to code
- Not assume root cause
- Not remove functionality unless required
- Not introduce hidden side effects
- Be structured and deterministic
- Ask clarification questions when ambiguity exists
- Avoid generic advice
- Be repo-aware
