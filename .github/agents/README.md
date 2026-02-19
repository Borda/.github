# GitHub Copilot Custom Agents

This directory contains **GitHub Copilot Custom Agents** for the **Borda** organization. These agents provide specialized AI assistants that can be invoked via `@` mentions in GitHub Copilot Chat.

## 📋 Available Agents

| Agent                                   | Slug             | Description                                                                  | Merge Block   |
| --------------------------------------- | ---------------- | ---------------------------------------------------------------------------- | ------------- |
| [SW Engineer](sw-engineer.agent.md)     | `@sw-engineer`   | Core logic architect focused on TDD, SOLID principles, and maintainable code | ❌            |
| [QA Specialist](qa-specialist.agent.md) | `@qa-specialist` | Testing strategist and edge case hunter ensuring code reliability            | ✅            |
| [Squeezer](squeezer.agent.md)           | `@squeezer`      | Performance optimizer focused on runtime efficiency and resource usage       | ❌            |
| [Doc-Scribe](doc-scribe.agent.md)       | `@doc-scribe`    | Documentation specialist ensuring comprehensive and up-to-date docs          | ✅ (releases) |
| [Mentor](mentor.agent.md)               | `@mentor`        | Contributor experience guide helping developers learn and succeed            | ❌            |

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
   name: agent-slug
   description: Short description for the Copilot dropdown
   tools:
     - github
   ---
   ```

2. **Markdown Body** - Agent instructions including:

   - Identity and role description
   - Philosophy and goals
   - Guidelines and rules
   - Permissions model
   - Tone guidelines
   - AI constraints

## 🔧 Adding or Modifying Agents

### Create a New Agent

1. Create a new file: `.github/agents/[slug].agent.md`
2. Add the YAML frontmatter with `name`, `description`, and `tools`
3. Write the agent instructions in markdown
4. Commit to `main` branch
5. Wait 1-2 minutes for GitHub to process

### File Naming Convention

- Filename format: `[slug].agent.md`
- The slug becomes the `@` mention (e.g., `qa-specialist.agent.md` → `@qa-specialist`)
- Use lowercase with hyphens for multi-word names

## 📚 Source Documentation

These agents are derived from the organization's [AGENTS.md](../../AGENTS.md) standards document, which defines:

- Agent roles and responsibilities
- Documentation protocols (6-point structure)
- Testing protocols (Borda Standard)
- Error handling protocols
- Security protocols
- Permissions model
- Handoff protocols

## 🔗 Official References

### GitHub Copilot Custom Agents

- [Creating Custom Agents for GitHub Copilot](https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot) - Official guide for creating custom agents
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot) - Main Copilot documentation hub
- [Copilot Chat](https://docs.github.com/en/copilot/using-github-copilot/asking-github-copilot-questions-in-your-ide) - Using Copilot Chat in your IDE

### Organization Configuration

- [Creating Default Community Health Files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) - How `.github` repositories work
- [Organization Repository Rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets) - Managing repository rules at org level

### Related Topics

- [GitHub Copilot for Business](https://docs.github.com/en/copilot/overview-of-github-copilot/about-github-copilot-for-business) - Enterprise features including custom agents
- [Managing Copilot Policies](https://docs.github.com/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-for-copilot-in-your-enterprise) - Organization-wide Copilot settings

## 🛠️ Troubleshooting

### Agent not appearing in dropdown

1. Ensure the file is in `.github/agents/` directory
2. Verify YAML frontmatter is valid and at the top of the file
3. Wait 1-2 minutes after committing to `main`
4. Try refreshing Copilot Chat

### Agent not responding correctly

1. Check the `name` field in frontmatter matches the filename slug
2. Verify the `tools:` section includes `- github`
3. Review the agent instructions for clarity

## 📝 Changelog

| Date       | Change                                      |
| ---------- | ------------------------------------------- |
| 2026-01-24 | Initial creation of 5 agents from AGENTS.md |

______________________________________________________________________

*These agents follow the [Borda Organization Standards](../../AGENTS.md) defined in the root AGENTS.md file.*
