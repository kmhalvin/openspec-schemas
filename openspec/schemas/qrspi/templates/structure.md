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
_Subagent: Based entirely on the decisions in `design.md`, outline the new types, function signatures, interfaces, or database models._

**Constraint**: Keep phases you're confident about high-level. Expand only where ambiguity is risky. If you think the implementing agent might get a phase wrong, expand that phase to show specific types and function signatures. Do NOT write full implementation code.

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
**Scope**: [which vertical slice]
**Key changes**:
- `[file/component]`: [what changes — new types, signatures, or brief description]
- `[file/component]`: [what changes]
**Verification**: [how to confirm this phase works]

### Phase 2: [Phase Name]
**Scope**: [which vertical slice]
**Key changes**:
- `[file/component]`: [what changes]
**Verification**: [how to confirm this phase works]

### Phase N: Testing & Polish
**Scope**: edge cases, error handling, cleanup
**Key changes**:
- [tests to add]
- [error handling to add]
**Verification**: [how to confirm this phase works]

## Out of Scope
_Subagent: Explicitly list what is NOT being changed or handled to prevent scope creep._

- [Out of scope item]
