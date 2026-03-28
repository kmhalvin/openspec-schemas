# Subagent Spec-Driven OpenSpec Schema

`subagent-spec-driven` is a workflow that applies **Frequent Intentional Compaction** — each phase (research, proposal, specs, design, tasks) runs in its own subagent with a fresh context window, producing structured artifacts that carry only the essential context forward.

The main agent prepares instructions (`*-prep` artifacts) which are then executed by a decoupled subagent, keeping context utilization lean by design.

- **Good fit**: Brownfield codebases, complex multi-step changes, teams that need human review gates between research/planning/implementation.
- **Not a good fit**: Simple one-shot changes where a single prompt and agent can just write the code directly without formal specification.

## Install (copy/paste)

Use the root `README.md` single-line install command with:
- `SCHEMA="subagent-spec-driven"`

## Activate & Configure

Set this schema and your subagent command in your `openspec/config.yaml`:

```yaml
schema: subagent-spec-driven

context: |
  Project rules for AI Agents:
  - Subagent CLI command: `gemini --yolo -p` # Replace with your project's subagent CLI command
```

OpenSpec automatically injects the `context` block into the Main Agent's prompt (as a `<project_context>` XML block or a JSON `context` field). The schema instructions tell the Main Agent to read this context to discover the correct command for spawning the subagent.

For example, using Claude or another AI tool:
```yaml
context: |
  Project rules for AI Agents:
  - Subagent CLI command: `claude text --prompt`
```

## Stage Gates

Artifact execution order:

```
research-proposal -> research-feasibility -> draft-proposal -> research-specs -> draft-specs -> research-design -> draft-design -> draft-tasks -> apply
```

Each phase follows a **prep → execute** pattern:

1. **`*-prep`** — Main agent reads dependency artifacts, writes detailed instructions for the subagent. Human reviews before spawning.
2. **`research-*` / `draft-*`** — Subagent executes in a fresh context window, produces a structured artifact, then halts.

This keeps each agent's context focused on its phase and creates natural human review checkpoints at the highest-leverage points (research and plans, not just code).

## Reference

- [Advanced Context Engineering for Coding Agents (ACE-FCA)](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/ace-fca.md)
- [Spec-Driven Development with Brownfield Projects](https://intent-driven.dev/blog/2026/03/10/spec-driven-development-brownfield/)
