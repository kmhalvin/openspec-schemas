# QRSPI Workflow Schema

The `qrspi` schema is an implementation of the ACE-FCA (Advanced Context Engineering for Coding Agents) "QRSPI" process, first presented by HumanLayer's Dex in the *"Everything We Got Wrong About RPI"* talk.

The core philosophy of QRSPI is avoiding large monolithic prompts that exhaust an LLM's "instruction budget", and instead prioritizing smaller checkpoints that humans can review without suffering from code-blindness.

## The Phases (Questions, Research, Design, Structure, Plan, Implement)

This schema is a sequential string of artifacts representing the QRSPI lifecycle natively running within OpenSpec's Directed Acyclic Graph (DAG) state machine.

To enable **Frequent Intentional Compaction (FIC)**, this schema isolates every single phase. Not only does it use a Main Agent -> Subagent handoff, but it forces a complete **Context Drop** (restarting the entire AI task session) after every major structural checkpoint. This completely eliminates instruction budget exhaustion and stops feature hallucination dead in its tracks.

### 1. Questions (`draft-questions-prep` -> `draft-questions`)
The main agent drafts instructions. The subagent scans the initial change request and outputs a `questions.md` file listing unknowns, ambiguities, or missing context. The subagent then halts.
**Human Action:** Open the file, answer the questions inline, and run `/opsx-continue`.

### 2. Research (`research-codebase-prep` -> `research-codebase`)
The subagent explores the codebase (guided blindly by the answered questions), compiling file lines, architecture patterns, and constraints. It outputs objective intelligence into `.research/codebase.md`.

### 3. Design (`draft-design-prep` -> `draft-design`)
Before outlining the code structure, the subagent dumps its brain into `design.md`. This contains the "Current State", the "Expected End State", and directly names the architectural patterns it found in Research that it intends to mimic.
**Human Action:** Perform "brain surgery" on the agent. If it highlights a bad or deprecated architectural pattern to follow, tell it "No, do not use that, use X instead" before it begins structural planning.

### 4. Structure Outline (`draft-structure-prep` -> `draft-structure`)
Relying entirely on the approved patterns in `design.md`, the subagent drafts a 1-2 page `structure.md` file. It resembles a C header file—showing only proposed function signatures, API interfaces, and high-level architectural steps.
**Human Action:** Review this short technical design doc to correct any bad API boundaries *before* the agent wastes time writing step-by-step tasks.

### 5. Plan (`draft-plan-prep` -> `draft-plan`)
Once `structure.md` is approved, the subagent generates a concrete execution checklist inside `plan.md`. Tasks are grouped by logical "vertical" phases, ensuring the AI implements a fully testable slice of code before touching other areas.

### 6. Implement (`apply`)
The agent actually writes the code, moving down its `plan.md` checklist and verifying against its self-defined success criteria.

## Subagent Requirements

This schema relies on a **Subagent** pattern to maintain context isolation.

If your agent (like Claude Code) provides subagents as a capability/tool (e.g. `Task()`), it will autonomously spawn them. If your agent is read-only or doesn't have parallel capabilities, you can provide an external CLI command in `openspec/config.yaml` to enforce sequential subagent execution:

```yaml
context: |
  Project rules for AI Agents:
  - Subagent CLI command: 'cline -y'
```
