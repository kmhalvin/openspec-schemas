<!--
  File: {ARTIFACT_ID}
  Phase: Subagent Preparation
  Change: {CHANGE_NAME}
-->

# Subagent Instructions: {CHANGE_NAME}

<!-- 
This file is created by the main agent to provide detailed instructions for a subagent.
MAIN AGENT INSTRUCTIONS:
1. Fill in the sections below based on the specific artifact being prepared.
2. IMPORTANT: You MUST replace `{ARTIFACT_ID}` and `{CHANGE_NAME}` placeholders with the exact string values from your execution context.
3. Since the next subagent starts empty, it absolutely needs full, literal paths to find files without guessing. Do not leave literal `{}` braces behind.
-->

## Objective

_Main Agent: State clearly what the Subagent must accomplish during this execution node._

[Objective]

## Context

_Main Agent: Summarize any relevant background information from previous artifacts that the Subagent strictly needs. If it's explicitly pulled from the 'requires' list, just tell the Subagent to read those files._

## Instructions

_Main Agent: Provide step-by-step instructions telling the Subagent exactly what to execute._

1. [Step 1]
2. [Step 2]
3. [Step 3]

## Expected Output

_Main Agent: Tell the Subagent to follow the provided template format from its CLI command context._
Follow the provided template from `openspec instructions {ARTIFACT_ID} --change {CHANGE_NAME}`.

**Output Path:** [Where the Subagent should save the file]

## References

_Main Agent: Provide absolute paths to any specific files, codebase patterns, or documentation the Subagent should immediately look at._

- [absolute_path_to_reference]
