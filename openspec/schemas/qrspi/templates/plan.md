<!--
  File: {ARTIFACT_ID}
  Phase: Plan
  Change: {CHANGE_NAME}
-->

# Implementation Plan: {CHANGE_NAME}

## Overview
[1-2 sentence summary of the verified structure outline]

## Scope Boundaries
_Main Agent: What are we explicitly NOT doing in this implementation?_
- [Out of scope item]

## Execution Plan

_Main Agent: List specific, actionable tasks mapped to the approved phases. Use `[ ]` checklist format. Tasks must be small enough to complete iteratively. Define clear success criteria for each task._

### Phase 1: [Phase Name]

#### Changes Required
_Main Agent: List specific, actionable tasks. Use `[ ]` checklist format. Tasks must be small enough to complete iteratively._

- [ ] **Task 1:** [Specific instruction]
  - **File:** `path/to/file.ext`
  - **Action:** [What exactly changes in this file?]
  
- [ ] **Task 2:** [Specific instruction]
  - **File:** `path/to/file.ext`
  - **Action:** [What exactly changes in this file?]

#### Success Criteria (Automated)
- [ ] Code compiles and type-checks (`npm run build`, `tsc`, `make`, etc.)
- [ ] Existing tests in area pass (`npm test`, `pytest`, etc.)

#### Success Criteria (Manual)
- [ ] User can manually verify X in the UI/CLI.

---

### Phase 2: [Phase Name]

#### Changes Required

- [ ] **Task 1:** [Specific instruction]
  - **File:** `path/to/file.ext`
  - **Action:** [What exactly changes in this file?]

#### Success Criteria / Verification:
_Main Agent: List the automated commands or manual steps required to verify this phase._

### Automated Checks:
- `[ ]` `make check` (or equivalent linter)
- `[ ]` `make test` (or equivalent test runner)
- `[ ]` `make build` (or equivalent build command)

### Manual Checks:
- `[ ]` [Specific manual verification step]

> **Pause for manual verification before proceeding to the next Phase.**

---

## Testing Strategy
_Main Agent: Provide the overarching strategy for how this implementation will be tested (Unit, E2E, Manual)._
- [Strategy details]
