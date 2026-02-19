# GitHub Copilot Custom Agents

Specialized AI assistants for the **Borda** organization, invoked via `@` mentions in GitHub Copilot Chat.

## Available Agents

| Agent                                   | Slug             | Tools                              | Description                                           |
| --------------------------------------- | ---------------- | ---------------------------------- | ----------------------------------------------------- |
| [SW Engineer](sw-engineer.agent.md)     | `@sw-engineer`   | read, edit, search, github         | Architecture, TDD, SOLID principles, code quality     |
| [QA Specialist](qa-specialist.agent.md) | `@qa-specialist` | read, edit, search, execute, github| Testing strategy, edge cases, test authoring          |
| [Squeezer](squeezer.agent.md)           | `@squeezer`      | read, search, execute, github      | Performance analysis and optimization with benchmarks |
| [Doc-Scribe](doc-scribe.agent.md)       | `@doc-scribe`    | read, edit, search, github         | Documentation authoring and synchronization           |
| [Mentor](mentor.agent.md)              | `@mentor`        | read, edit, search, github         | Contributor experience, PR feedback, agent routing    |

## How to Invoke

In GitHub Copilot Chat (VS Code, GitHub.com, JetBrains, CLI):

```
@sw-engineer Review this function for SOLID principle violations
@qa-specialist What edge cases should I test for this parser?
@squeezer Profile and identify the bottleneck in this query loop
@doc-scribe Write a 6-point docstring for this function
@mentor I'm new to this project, where should I start?
```

`@mentor` can also route you directly to specialist agents via its configured handoffs.

## Agent Selection

| When you need...                              | Use              |
| --------------------------------------------- | ---------------- |
| Architecture decisions, code structure        | `@sw-engineer`   |
| Test coverage, edge case identification       | `@qa-specialist` |
| Performance analysis, optimization            | `@squeezer`      |
| API docs, README updates, docstrings          | `@doc-scribe`    |
| Onboarding, PR feedback, routing to a specialist | `@mentor`    |

## File Structure

Each agent is a `.agent.md` file with YAML frontmatter and a markdown body (max 30,000 chars).

### Frontmatter Schema

```yaml
---
name: agent-slug              # optional; defaults to filename slug
description: "..."            # required — shown in Copilot dropdown
tools:                        # omit to enable all tools
  - read                      # read file contents
  - edit                      # write/edit files
  - search                    # grep/glob code search
  - execute                   # run shell commands (VS Code / coding agent)
  - github                    # GitHub MCP server (issues, PRs, code)
agents:                       # agents this agent can invoke
  - other-agent-slug
handoffs:                     # guided transitions to other agents
  - label: "Label shown to user"
    agent: target-agent-slug
    prompt: "Prompt sent to the target agent"
target: vscode                # optional: restrict to "vscode" or "github-copilot"
infer: true                   # optional: allow automatic agent selection (default true)
---
```

Other supported fields: `model`, `argument-hint`, `user-invokable`, `mcp-servers`, `metadata`.

### Markdown Body

Defines agent behavior: identity, philosophy, responsibilities, context discovery rules, and constraints.

## What Agents Can and Cannot Do

These are **Copilot Chat assistants** — they respond to questions, use tools, and produce output. They are not autonomous agents with access control privileges.

| Capability                                    | Supported |
| --------------------------------------------- | --------- |
| Read files and search code                    | ✅        |
| Write/edit files (`edit` tool)                | ✅        |
| Run shell commands (`execute` tool)           | ✅ (VS Code / coding agent context) |
| Query GitHub API (issues, PRs, code)          | ✅        |
| Route to other agents (`handoffs`)            | ✅ (configured in `mentor`) |
| Approve pull requests                         | ❌        |
| Merge or block pull requests                  | ❌        |
| Push to protected branches                    | ❌        |

> Merge control and branch protection are configured via [GitHub rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), not agent files.

## Adding or Modifying Agents

1. Create `.github/agents/[slug].agent.md`
2. Add YAML frontmatter with at minimum `description` and `tools`
3. Write agent instructions in markdown
4. Commit to `main` — active after ~1–2 minutes

**Naming**: lowercase with hyphens; allowed characters: `.`, `-`, `_`, `a-z`, `A-Z`, `0-9`

## Troubleshooting

| Symptom                        | Fix                                                          |
| ------------------------------ | ------------------------------------------------------------ |
| Agent not in dropdown          | Verify file is in `.github/agents/`, frontmatter is valid, wait 2 min |
| Agent ignores tool              | Check `tools:` list includes the tool you need              |
| Handoffs not appearing         | Verify `agents:` and `handoffs:` frontmatter in the source agent |
| Agent responds generically     | Add project-specific conventions to the agent body           |

## Official References

- [About custom agents](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents)
- [Custom agents configuration reference](https://docs.github.com/en/copilot/reference/custom-agents-configuration)
- [Creating custom agents](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents)
- [GitHub Copilot documentation](https://docs.github.com/en/copilot)
- [Organization rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)

## Changelog

| Date       | Change                                                         |
| ---------- | -------------------------------------------------------------- |
| 2026-02-19 | Rewrite all agents: fix tools, remove boilerplate, wire mentor handoffs |
| 2026-02-19 | Align tools and capabilities with GH docs; remove fictional permissions |
| 2026-01-24 | Initial creation of 5 agents from AGENTS.md                    |

---

*These agents follow [Borda Organization Standards](../../AGENTS.md).*
