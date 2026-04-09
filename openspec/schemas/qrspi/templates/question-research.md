<!--
  File: {ARTIFACT_ID}
  Phase: Pre-Question Codebase Alignment
  Change: {CHANGE_NAME}
-->

# Codebase Alignment Context: {CHANGE_NAME}

## Objective
_Subagent: Based on the provided context, deeply explore the codebase to map out the current components. You are NOT designing the feature entirely, but you MUST dig deep enough to formulate highly specific, file-based technical questions._

## Proposed Search Boundaries
_Subagent: What exact files, directories, or architectural patterns did you find that the deeper Research phase should investigate? Outline your PROPOSED boundaries. Note that these are not final; the Main Agent and user will adjust these boundaries based on the answers to your questions in the next phase._
- `[file/module/pattern]` -> [Why the next phase needs to read/understand this]
- `[file/module/pattern]` -> [Why the next phase needs to read/understand this]

## Deep Technical Questions (CRITICAL)
_Subagent: Formulate highly specific, codebase-rooted questions for the user to answer. These must be detailed. For example, rather than "How do we handle payments?", ask "The ticket mentions integrating Stripe, but `payment.ts` currently uses a hardcoded PayPal SDK instance. Are we replacing Paypal entirely, or building a factory to support both?"_
- **Question 1**: [Deep Context] - [Specific Question?]
- **Question 2**: [Deep Context] - [Specific Question?]
