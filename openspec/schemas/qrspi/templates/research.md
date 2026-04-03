<!--
  File: {ARTIFACT_ID}
  Phase: Research
  Change: {CHANGE_NAME}
-->

# Codebase Research: {CHANGE_NAME}

## Critical Rule
_Main Agent: Your output must be 100% factual. Document what exists, how it works, and where it lives. ZERO OPINIONS. ZERO SUGGESTIONS. ZERO IMPLEMENTATION IDEAS. Do not critique code quality, and do not editorialize._

## Objective Findings
_Main Agent: Answer the assigned research questions factually, using exact file:line references._

### Question: [Paste Question 1]
[Factual answer detailing what exists and how it works]
- **File:** `path/to/file.ext:start-end`

### Question: [Paste Question 2]
[Factual answer detailing what exists and how it works]
- **File:** `path/to/file.ext:start-end`

## Code References Database
_Main Agent: Create an index of every single file you looked at that is relevant to the topics above, so downstream agents can find them instantly._

- `path/to/file.ext:123` - [Brief description of what exists here]
- `path/to/file.ext:456` - [Brief description of what exists here]

## Patterns Found
_Main Agent: Document any existing codebase patterns discovered during this research (e.g., "The API uses a repository pattern", "Errors are handled using a central middleware"). Document these without judgment._

- **Pattern:** [Description]
- **Location:** `path/to/file.ext`
