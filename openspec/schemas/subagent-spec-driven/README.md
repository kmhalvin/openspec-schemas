# Subagent Spec-Driven OpenSpec Schema

`subagent-spec-driven` is a workflow that applies **Frequent Intentional Compaction** — each phase (research, proposal, specs, design, tasks) runs in its own subagent, producing structured artifacts that carry only the essential context forward.

The main agent prepares instructions (`*-prep` artifacts) which are then executed by a subagent, keeping context utilization lean by design.

- **Good fit**: Brownfield codebases, complex multi-step changes, teams that need human review gates between research/planning/implementation.
- **Not a good fit**: Simple one-shot changes where a single prompt and agent can just write the code directly without formal specification.

## Install (copy/paste)

Use the root `README.md` single-line install command with:
- `SCHEMA="subagent-spec-driven"`

## Activate & Configure

Set this schema in your `openspec/config.yaml`:

```yaml
schema: subagent-spec-driven
```

### Subagent Spawning

The schema instructions tell the main agent to spawn a subagent after each `*-prep` step. How this works depends on your agent tool:

**If your agent has a built-in subagent tool** (e.g. Claude Code's `Task()`, or similar), you don't need any extra configuration — the main agent already knows how to spawn subagents. The schema instructions will guide it to use its native subagent capabilities.

**If your agent requires a CLI command** to spawn a subagent, define it in your project context so the main agent can discover it:

```yaml
schema: subagent-spec-driven

context: |
  Project rules for AI Agents:
  - Subagent CLI command: `gemini --yolo -p`
```

OpenSpec injects the `context` block into the main agent's prompt (as a `<project_context>` XML block or a JSON `context` field), so the schema instructions can reference it.

### Subagent Requirements

The subagent must be capable of:
- **Reading files** — dependency artifacts, codebase files, existing specs
- **Writing files** — producing research findings, proposals, specs, design docs, task lists
- **Executing commands** — running `openspec instructions` to retrieve its template and context

Some agents provide subagents with **read-only access** (e.g. Cline's built-in subagent can read files but cannot write or execute commands). In that case, you need an external subagent CLI with full capabilities. Define it in your project context:

```yaml
context: |
  Project rules for AI Agents:
  - Subagent CLI command: `cline -y`
```

The subagent is **not** starting from scratch. Because the spawn prompt injected by the main agent executes the `/opsx-continue` command, the subagent will naturally use its available tools or skills to retrieve the full OpenSpec workflow context: dependencies (with absolute paths and status), the template to follow, and the schema instructions. The subagent's job is to read the provided dependencies, explore the codebase as needed, and produce the target artifact.

## Stage Gates

Artifact execution order:

```
research-proposal -> research-feasibility -> draft-proposal -> research-specs -> draft-specs -> research-design -> draft-design -> draft-tasks -> apply
```

Each phase follows a **prep → execute** pattern:

1. **`*-prep`** (Main Agent) — Reads completed dependency artifacts and writes detailed instructions for the subagent. The main agent doesn't need a subagent for this step — it has enough context from reading dependencies to craft good instructions. Human reviews before spawning.
2. **`research-*` / `draft-*`** (Subagent) — Receives OpenSpec workflow context (dependencies, template, instructions), reads dependency artifacts for understanding, explores the codebase for deep research, then produces a structured artifact and halts.

This creates natural human review checkpoints at the highest-leverage points — research and plans rather than just code.

## Reference

- [Advanced Context Engineering for Coding Agents (ACE-FCA)](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/ace-fca.md)
- [Spec-Driven Development with Brownfield Projects](https://intent-driven.dev/blog/2026/03/10/spec-driven-development-brownfield/)
