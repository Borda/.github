# GitHub Copilot Custom Agents

This directory contains **GitHub Copilot Custom Agents** for the **Borda** organization. These agents provide specialized AI assistants that can be invoked via `@` mentions in GitHub Copilot Chat.

## 📋 Available Agents

| Agent                                   | Slug             | Description                                                                  |
| --------------------------------------- | ---------------- | ---------------------------------------------------------------------------- |
| [SW Engineer](sw-engineer.agent.md)     | `@sw-engineer`   | Core logic architect focused on TDD, SOLID principles, and maintainable code |
| [QA Specialist](qa-specialist.agent.md) | `@qa-specialist` | Testing strategist and edge case hunter ensuring code reliability            |
| [Squeezer](squeezer.agent.md)           | `@squeezer`      | Performance optimizer focused on runtime efficiency and resource usage       |
| [Doc-Scribe](doc-scribe.agent.md)       | `@doc-scribe`    | Documentation specialist ensuring comprehensive and up-to-date docs          |
| [Mentor](mentor.agent.md)               | `@mentor`        | Contributor experience guide helping developers learn and succeed            |

## 🚀 How It Works

### Invoking an Agent

In GitHub Copilot Chat (VS Code, GitHub.com, or CLI), type `@` followed by the agent name:

```
@sw-engineer Review this function for SOLID principle violations
@qa-specialist What edge cases should I test for this parser?
@squeezer How can I optimize this database query?
@doc-scribe Help me write documentation for this API endpoint
@mentor I'm new to this project, where should I start?
```

### Agent Selection Guide

| When you need...                              | Use              |
| --------------------------------------------- | ---------------- |
| Architecture decisions, code structure advice | `@sw-engineer`   |
| Test coverage, edge case identification       | `@qa-specialist` |
| Performance analysis, optimization tips       | `@squeezer`      |
| API documentation, README updates             | `@doc-scribe`    |
| Onboarding help, PR feedback summary          | `@mentor`        |

## 📁 File Structure

Each agent is defined in its own `.agent.md` file with:

1. **YAML Frontmatter** - Required metadata:

   ```yaml
   ---
   name: agent-slug           # optional; defaults to filename slug
   description: Short description for the Copilot dropdown  # required
   tools:                     # omit to enable all tools
     - read                   # read file contents
     - edit                   # write/edit files
     - search                 # grep/glob code search
     - github                 # GitHub MCP server (issues, PRs, code)
   ---
   ```

   Other supported frontmatter fields: `target`, `infer`, `model`, `argument-hint`, `user-invokable`, `agents`, `handoffs`, `mcp-servers`, `metadata`.

2. **Markdown Body** - Agent instructions including:

   - Identity and role description
   - Philosophy and goals
   - Guidelines and rules
   - Capabilities (what the agent can and cannot do)
   - Tone guidelines
   - AI constraints

## 🔧 Adding or Modifying Agents

### Create a New Agent

1. Create a new file: `.github/agents/[slug].agent.md`
2. Add the YAML frontmatter with at least `description` and `tools`
3. Write the agent instructions in markdown (max 30,000 characters)
4. Commit to `main` branch
5. Wait 1-2 minutes for GitHub to process

### File Naming Convention

- Filename format: `[slug].agent.md`
- The slug becomes the `@` mention (e.g., `qa-specialist.agent.md` → `@qa-specialist`)
- Use lowercase with hyphens for multi-word names; allowed characters: `.`, `-`, `_`, `a-z`, `A-Z`, `0-9`

### What Agents Can and Cannot Do

These are **Copilot Chat assistants** — they respond to questions and use tools to provide guidance. They are **not** autonomous agents with access control privileges.

| Capability                           | Supported |
| ------------------------------------ | --------- |
| Read files and search code           | ✅ Yes    |
| Comment on issues and PRs            | ✅ Yes    |
| Write/edit files (with `edit` tool)  | ✅ Yes    |
| Query GitHub API (issues, PRs, code) | ✅ Yes    |
| Approve pull requests                | ❌ No     |
| Block or merge pull requests         | ❌ No     |
| Push to protected branches           | ❌ No     |

> Merge control and branch protection are configured separately via [GitHub rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), not via agent files.

## 📚 Source Documentation

These agents are derived from the organization's [AGENTS.md](../../AGENTS.md) standards document, which defines:

- Agent roles and responsibilities
- Documentation protocols (6-point structure)
- Testing protocols (Borda Standard)
- Error handling protocols
- Security protocols
- Handoff protocols

## 🔗 Official References

### GitHub Copilot Custom Agents

- [About custom agents](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents) - What custom agents are and how they work
- [Custom agents configuration reference](https://docs.github.com/en/copilot/reference/custom-agents-configuration) - Full YAML frontmatter schema
- [Creating custom agents](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents) - Step-by-step guide
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot) - Main Copilot documentation hub

### Organization Configuration

- [Creating Default Community Health Files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) - How `.github` repositories work
- [Organization Repository Rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets) - Managing repository rules at org level

## 🛠️ Troubleshooting

### Agent not appearing in dropdown

1. Ensure the file is in `.github/agents/` directory
2. Verify YAML frontmatter is valid and at the top of the file
3. Wait 1-2 minutes after committing to `main`
4. Try refreshing Copilot Chat

### Agent not responding correctly

1. Check the `name` field in frontmatter matches the filename slug
2. Verify the `tools:` section lists the capabilities you need (e.g., `- read`, `- github`)
3. Review the agent instructions for clarity

## 📝 Changelog

| Date       | Change                                           |
| ---------- | ------------------------------------------------ |
| 2026-02-19 | Align tools and capabilities with GH docs        |
| 2026-01-24 | Initial creation of 5 agents from AGENTS.md      |

______________________________________________________________________

*These agents follow the [Borda Organization Standards](../../AGENTS.md) defined in the root AGENTS.md file.*
