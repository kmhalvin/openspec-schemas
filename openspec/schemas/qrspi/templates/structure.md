<!--
  File: {ARTIFACT_ID}
  Phase: Structure Outline
  Change: {CHANGE_NAME}
-->

# Structure Outline: {CHANGE_NAME}

## Overview
_Subagent: Provide a brief summary of how the approved `design.md` will be implemented structurally._

[Summary here]

## High-Level Architecture (C Header Style)
_Subagent: Based entirely on the decisions in `design.md`, outline the new types, function signatures, interfaces, or database models. This is NOT the implementation code, just the structural definitions so the user can verify the API interface before step-by-step tasks are written._

```typescript
// Example:
// interface NewFeature { ... }
// function initFeature(): void;
```

## Proposed Phases (Vertical Slices)
_Subagent: Break the change down into high-level phases of execution._

> [!WARNING]
> DO NOT write a "Horizontal Plan" (e.g., Phase 1: All Database tables, Phase 2: All APIs, Phase 3: All Frontend). Models love doing this, and it results in 1,200 lines of broken code that is impossible to test until the very end.

_Subagent: You MUST write a "Vertical Plan". Build complete, testable slices.
Example Vertical Flow:
- Phase 1: Mock API endpoint and get it working in the frontend.
- Phase 2: Wire the frontend to the mock.
- Phase 3: Mock out the services layer.
- Phase 4: Do the real database migration and wire everything together._

### Phase 1: [Phase Name]
- **Goal**: [What does this phase achieve?]
- **Test Checkpoint**: [How will we verify this phase works before moving to Phase 2?]
- **Key Files**: [Files touched in this phase]

### Phase 2: [Phase Name]
- **Goal**: [What does this phase achieve?]
- **Test Checkpoint**: [How will we verify this phase works?]
- **Key Files**: [Files touched in this phase]

### Phase 3: [Phase Name]
- ...

## Out of Scope
_Subagent: Explicitly list what is NOT being changed or handled to prevent scope creep._

- [Out of scope item]
