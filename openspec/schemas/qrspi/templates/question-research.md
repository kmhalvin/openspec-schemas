<!--
  File: {ARTIFACT_ID}
  Phase: Pre-Question Codebase Alignment
  Change: {CHANGE_NAME}
-->

# Codebase Alignment Context: {CHANGE_NAME}

## Objective
_Subagent: Based exclusively on the initial ticket/goal, briefly explore the codebase to map out the current components. You are NOT designing the feature yet. Your sole task is to gather enough technical context so the Main Agent can formulate high-quality, targeted architectural questions for the human._

## Existing Components Discovered
_Subagent: What exact files or modules are relevant to the requested change?_
- `[file/module]` -> [Brief description of what it does]
- `[file/module]` -> [Brief description of what it does]

## Found Ambiguities / Missing Context
_Subagent: What did you find in the codebase that immediately conflicts with or complicates the ticket? Provide explicit file findings that the Main Agent should ask the human about._
- **Ambiguity 1**: [Description + Context]
- **Ambiguity 2**: [Description + Context]
