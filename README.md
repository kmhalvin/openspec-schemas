# OpenSpec Schemas

Welcome to the **OpenSpec Schemas** repository! This is a collection of workflow schemas for OpenSpec, the context engineering and orchestrator CLI for AI Coding Agents.

These schemas define structured workflows to help AI agents (like Claude Code, Cursor, Cline, or Gemini) navigate complex changes, execute step-by-step reasoning, and maintain high-leverage alignment with human developers.

## Available Schemas

### `subagent-spec-driven`
A powerful Spec-Driven Development framework designed for complex, brownfield codebases. It applies **Frequent Intentional Compaction** by separating work into discrete phases (research, proposal, specifications, design, implementation tasks). 

It utilizes a Main Agent to formulate instructions, and a Subagent to execute them in isolated context windows, effectively keeping context utilization lean.

- **Learn more**: [subagent-spec-driven documentation](./openspec/schemas/subagent-spec-driven/README.md)

## Installation

You can install schemas from this repository directly into your OpenSpec workspace.

For example, to install the `subagent-spec-driven` schema, run this single-line command in the root of your project:

```bash
SCHEMA="subagent-spec-driven" && mkdir -p openspec/schemas/$SCHEMA && curl -sSL https://raw.githubusercontent.com/kmhalvin/openspec-schemas/main/openspec/schemas/$SCHEMA/schema.yaml -o openspec/schemas/$SCHEMA/schema.yaml && curl -sSL "https://api.github.com/repos/kmhalvin/openspec-schemas/contents/openspec/schemas/$SCHEMA/templates" | grep '"download_url"' | cut -d '"' -f 4 | xargs -n 1 -I {} sh -c 'mkdir -p "openspec/schemas/'$SCHEMA'/templates" && curl -sSL "{}" -o "openspec/schemas/'$SCHEMA'/templates/$(basename "{}")"'
```

After installation, update your `openspec/config.yaml` to point to the newly downloaded schema.

## Contributing

We welcome community contributions! If you have developed an OpenSpec schema that drastically improves your workflow or solves a niche problem (like test-driven execution, CI/CD automated review gating, etc.), please open a Pull Request.

When introducing a new schema, ensure you provide:
1. The `schema.yaml` defining the node execution flow.
2. The `templates/` directory containing all markdown prompts needed.
3. A `README.md` that explains the workflow, best use cases, and required agent capabilities.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
