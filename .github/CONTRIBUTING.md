# Contributing Guide

Thank you for your interest in contributing! We appreciate all contributions and welcome everyone, regardless of experience level. Your help makes this project better for everyone.

> [!TIP]
> **First time contributing to open source?** Check out [First Contributions](https://github.com/firstcontributions/first-contributions) for a beginner-friendly guide that walks you through the entire process.

> [!NOTE]
> **Configuration files are the source of truth.** If this documentation ever contradicts `pyproject.toml`, `.pre-commit-config.yaml`, or other config files, trust the config. Please open an issue so the docs can be corrected.

## 📜 Code of Conduct

Please read and follow our [Code of Conduct](CODE_OF_CONDUCT.md). We expect all contributors to be respectful, considerate, and help create a welcoming environment for everyone. This ensures our community remains inclusive and supportive for people from all backgrounds.

## 🎯 Ways to Contribute

There are many ways to contribute beyond writing code. Every contribution, no matter how small, makes a difference:

| Contribution            | Description                                                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 🐛 Report bugs          | Found an issue? Let us know! Detailed bug reports help us fix problems faster.                                                  |
| 🛠️ Fix bugs             | Implement fixes for reported issues. Great way to start contributing!                                                           |
| 💡 Suggest improvements | Propose enhancements, optimizations, or better approaches to existing functionality                                             |
| ✨ Build features       | Implement new features after getting maintainer approval                                                                        |
| 📖 Improve docs         | Fix typos, clarify explanations, or add examples. Good documentation makes the project accessible to more people.               |
| 👀 Review PRs           | Provide feedback on pull requests. Code reviews help maintain quality and catch potential issues early.                         |
| 💬 Answer questions     | Help others in discussions and issues. Your knowledge can help someone overcome a problem.                                      |
| ⭐ Spread the word      | Star the repo, share it with others, or write about your experience. This helps the project grow and attract more contributors. |

## 💬 Before You Start

### Read First

Taking time to understand the project first helps you contribute more effectively:

- **Documentation** – Learn how the project works and its key concepts. This prevents misunderstandings and ensures your contributions align with project goals.
- **Existing issues** – Your idea might already be discussed or even implemented. Searching first saves you time and effort.
- **Codebase** – Familiarize yourself with the code structure and style. This makes it easier to make changes that fit well with the existing code.

### Ask Questions

Don't hesitate to ask! Open an issue or use discussions to:

- Clarify project goals and scope – Make sure your contributions are aligned with the project's direction
- Understand implementation details – Get help with specific technical questions
- Get guidance on where to contribute – Find areas where your skills and interests can make the biggest impact

> [!NOTE]
> Asking questions shows you're thoughtful and helps everyone learn together.

## 🐛 Reporting Bugs

When reporting a bug, providing clear and detailed information helps us fix it faster. Here's how:

1. **Search existing issues** – The bug might already be reported and being worked on.
2. **Create a minimal reproduction** – Provide a simple example that demonstrates the bug. This makes it easier for us to reproduce and fix the issue.
3. **Include environment details** – Tell us your operating system, relevant runtime or application version, and any other important tools or dependencies (for example, database, browser, CLI, or framework versions).
4. **Describe expected vs actual behavior** – Be specific about what you expected to happen and what actually occurred.

## 🛠️ Fixing Bugs

Bug fixing is a great way to contribute! Here's how to get started:

1. **Find a bug to fix** – Look for issues labeled `bug` or `help wanted` in the issue tracker.
   - Check if the issue is already assigned to someone
   - If it's assigned but has no activity for a while, comment to ask if you can take it over
2. **Understand the problem** – Read the issue carefully and try to reproduce the bug.
3. **Investigate and fix** – Identify the root cause and implement a fix. Keep your changes focused on the specific issue.
4. **Test your fix** – Write or update tests to verify your fix works and prevents the bug from recurring.
5. **Submit a PR** – Create a pull request with your fix, linking to the issue it addresses.

> [!TIP]
> Fixes with tests are more likely to be merged quickly!

## 💡 Suggesting Improvements

Improvements are enhancements to existing functionality that make the project better. They could be:

- Performance optimizations
- Code refactoring for better maintainability
- User experience enhancements
- Documentation improvements
- Process or workflow improvements

Here's how to suggest and implement improvements:

1. **Open an issue** – Describe the improvement you're suggesting. Explain the current situation, why it needs improvement, and your proposed solution.
2. **Provide context** – Include examples, use cases, or data to support your suggestion.
3. **Discuss and refine** – Engage in the issue discussion to clarify requirements and explore alternatives.
4. **Get feedback** – Wait for input from maintainers and the community. For small improvements, you may get rapid approval.
5. **Implement if approved** – If your suggestion is accepted, follow the standard development process.

## ✨ Building Features with Consensus

**Before implementing any new feature:**

1. **Open an issue first** – Clearly describe your idea, use case, and how it benefits the project.
   - Check if the issue is already assigned to someone
   - If it's assigned but has no activity for a while, comment to ask if you can take it over
2. **Wait for maintainer approval** – Look for a **👍 "go-ahead" reaction** or explicit approval from a maintainer.
3. **Discuss and refine** – Engage in the issue discussion to clarify requirements and explore alternatives.
4. **Get consensus** – Ensure there's general agreement from the community before starting implementation.

> [!CAUTION]
> Always get maintainer approval before implementing new features! This ensures your work aligns with project direction and won't be wasted effort. Features implemented without prior approval may be rejected.

**When you have approval:**

1. **Implement the feature** – Build the feature following the project's coding style and guidelines.
2. **Add tests** – Write comprehensive tests to ensure your feature works correctly.
3. **Update documentation** – Document how to use the new feature.
4. **Submit a PR** – Create a pull request, linking to the approved issue.

## 🔀 Pull Requests

### Before Opening a PR

Complete this checklist before opening a pull request to ensure quality and smooth review:

- [ ] Followed existing code style
- [ ] Added tests for new functionality
- [ ] Ran tests locally and they pass
- [ ] Updated documentation if needed
- [ ] Self-reviewed my code
- [ ] Linked to related issue(s)

### Linking Issues

**Every PR should reference an issue.** This provides context and helps track progress. Use keywords like:

- `Fixes #123` – Closes the issue when PR is merged
- `Relates to #456` – Links without auto-closing

If no issue exists, open one first to discuss the change before implementing it.

### Keep PRs Focused

- **One PR = one logical change** – This makes your PR easier to review and understand
- **Smaller PRs are easier to review** – Large PRs can be overwhelming and take longer to merge
- **Split large changes into multiple PRs** – Break complex features into smaller, manageable pieces

### Reviewing PRs

When reviewing a pull request, follow this structured format to give consistent, actionable feedback.

**Overall recommendation** — open with one of:

- 🟢 **Approve** — Ready to merge as-is
- 🟡 **Minor Suggestions** — Non-blocking improvements recommended
- 🟠 **Request Changes** — Issues must be addressed before merge
- 🔴 **Block** — Critical problems require major rework

Include a one-sentence justification. Example: `🟠 Request Changes — Missing tests for error path and docstring not in Google style.`

**Completeness checklist** — mark each: ✅ Complete / ⚠️ Incomplete / ❌ Missing / 🔵 N/A

- [ ] Clear description of what changed and why
- [ ] Linked to a related issue (`Fixes #NNN` or `Relates to #NNN`)
- [ ] Tests added/updated (happy path, failure path, edge cases)
- [ ] Google-style docstrings for all new/changed public APIs
- [ ] No secrets or credentials introduced
- [ ] Linting and CI checks pass

**Quality scoring (n/5)** across three dimensions:

| Score  | Meaning                                      |
| :----- | :------------------------------------------- |
| 5/5 🟢 | Excellent — no issues                        |
| 4/5 🟢 | Good — minor improvements possible           |
| 3/5 🟡 | Adequate — some gaps to address              |
| 2/5 🟠 | Needs Work — multiple problems               |
| 1/5 🔴 | Poor / Missing — significant rework required |

Score **Code Quality** (correctness, type hints, idioms), **Testing** (coverage, edge cases, assertion specificity), and **Documentation** (docstrings, examples, changelog).

**Risk assessment** — flag explicitly with severity (1–5):

- **Breaking changes** — API signature changes, removed features; must include migration notes
- **Performance** — O(n²) loops, memory-heavy operations on large arrays
- **Security** — unvalidated input, credential exposure
- **Compatibility** — new Python version requirements, new heavy dependencies

**Review summary template:**

```
## Review Summary

### Recommendation
[emoji] [Status] — [One-sentence justification]

### Completeness
- ✅ [items complete]
- ❌ [items missing]

### Quality Scores
- Code: n/5 [emoji] — [reason]
- Testing: n/5 [emoji] — [reason]
- Documentation: n/5 [emoji] — [reason]

### Risk: n/5 [emoji] — [brief description]

### Must Fix
1. [Specific issue — link to inline comment]

### Suggestions (non-blocking)
1. [Optional improvement — link to inline suggestion]

### Next Steps
1. [Clear action item for the author]
```

**Best practices:**

- Use GitHub inline comments and `suggestion` blocks on the code itself; reference their permalinks in the summary.
- Explain *why* something is a problem, not just *what* is wrong.
- Distinguish blocking issues from nice-to-haves.
- Acknowledge good work — don't only list problems.
- Defer style nitpicks to automated tools (`ruff`, `pre-commit`); don't block PRs on what linters can auto-fix.

## ✅ Tests and Quality Assurance

Tests and quality improvements are **always welcome**! These contributions are highly valuable because they:

- Improve project stability – Well-tested code is more reliable for everyone
- Help catch future regressions – Tests prevent issues from reoccurring
- Reduce maintainer burden – Comprehensive tests require less ongoing debugging

For information about testing when fixing bugs, see the [Fixing Bugs](#-fixing-bugs) section.

## 🐍 Development Standards

This section defines the technical baseline for Python projects in this organization. A specific project's `CONTRIBUTING.md` may extend or override these defaults.

### Code Style

- **Type hints** — All new functions and methods must include type annotations.
- **Linting** — Code must pass `ruff` checks. Run `pre-commit run --all-files` before committing.
- **Naming** — Follow PEP 8: `snake_case` for functions/variables, `PascalCase` for classes.
- **Imports** — Order: standard library → third-party → local (enforced by `ruff --select I`).
- **Clarity over cleverness** — Write code that is easy to read and debug, even if slightly more verbose.

### Documentation

Every public class and function must include a docstring following [Google style](https://google.github.io/styleguide/pyguide.html#383-functions-and-methods) with these sections:

1. **Summary** — One-line description of what it does.
2. **Description** — *(required for non-trivial functions)* Algorithm, assumptions, or non-obvious behaviors. Omit for trivially self-evident functions.
3. **Args** — Parameters with types and descriptions.
4. **Returns** — Return value and type.
5. **Raises** — Exceptions that may be raised.
6. **Examples** — Executable `>>>` doctests demonstrating usage.

```python
def filter_values(data: list[float], threshold: float = 0.5) -> list[float]:
    """Filter values above a threshold.

    Args:
        data: Input values to filter.
        threshold: Minimum value to retain. Must be non-negative.

    Returns:
        List of values strictly above the threshold.

    Raises:
        ValueError: If threshold is negative.

    Examples:
        >>> filter_values([0.1, 0.6, 0.9], threshold=0.5)
        [0.6, 0.9]
        >>> filter_values([])
        []
    """
```

### Testing

- **Test-driven** — Write a failing test before fixing a bug or implementing a feature.
- **Doctests** — Executable `>>>` examples in docstrings serve as first-line unit tests.
- **Edge cases** — Always cover: `None`, empty inputs (`[]`, `""`), zero/negative values, and boundary conditions.
- **Specific assertions** — Tests must catch plausible-but-wrong outputs; "no exception raised" is insufficient.

> [!TIP]
> When reviewing a test, ask: "If this function returned a wrong but plausible value, would this test catch it?" If not, improve the assertion.

### Error Handling

- **Fail fast** — Raise exceptions early; never return magic error codes.
- **Contextual messages** — Include relevant state in error messages (e.g., input values, expected vs. actual).
- **No silent failures** — Every caught exception must be logged or re-raised.
- **Custom exceptions** — Use domain-specific exception classes where it aids clarity.

### Security

- Never commit `.env` files, API keys, or credentials — use environment variables or secret managers.
- Validate and sanitize all external input (CLI args, file uploads, API responses).
- Prefer `ruff --select S` for Python security linting in CI.
- Follow the principle of least privilege: request only the access your code actually needs.

### ML / AI Research Specifics

- **Reproducibility** — Use fixed random seeds; pin dataset versions and model configs.
- **Data validation** — Assert tensor shapes, dtypes, and value ranges before processing.
- **Lazy loading** — Prefer deferred imports and on-demand computation for large models/datasets.
- **Experiment logging** — Track hyperparameters, metrics, and environment details for every run.

### Language Adaptation

These standards apply across all languages used in Borda projects. Adapt tooling per stack:

| Language      | Type Safety        | Doctests        | Linting          | Security Scan       |
| :------------ | :----------------- | :-------------- | :--------------- | :------------------ |
| Python        | `typing` module    | `>>> ` blocks   | `ruff`           | `ruff --select S`   |
| Rust          | Static types       | `///` doc-tests | `clippy`         | `cargo audit`       |
| JS/TypeScript | TypeScript / JSDoc | JSDoc examples  | ESLint, Prettier | `npm audit`, `snyk` |
| Go            | Static types       | `Example` funcs | `golangci-lint`  | `govulncheck`       |

### Code Markers (TODO / FIXME)

Leave structured comments so that intent and status are visible in the code itself — the next contributor or agent can determine what still needs doing without reading conversation history.

| Marker       | Meaning                                                                                             |
| :----------- | :-------------------------------------------------------------------------------------------------- |
| `TODO(wip):` | Work is **incomplete** — must be continued before this can be considered done.                      |
| `TODO:`      | Work is done, but a worthwhile follow-up was spotted — scoped observation, not blocking.            |
| `FIXME:`     | Work is done, but there is a suspected related issue with high confidence — deserves a closer look. |

```python
# TODO(wip): implement retry logic — stub written, needs exponential backoff
# TODO: consider LRU cache here once usage patterns are clearer
# FIXME: assumes sorted input — verify upstream always guarantees order
```

**Rules:**

- Remove `TODO(wip):` in the **same commit** when the referenced work is complete — never leave it dangling.
- `TODO:` and `FIXME:` may persist until addressed in a follow-up issue or PR; open an issue if the concern is significant.
- All three are greppable: `grep -r "TODO\|FIXME" .`

## 💎 Quality Expectations

> [!IMPORTANT]
> **Always do your best – that's the essential spirit of OSS contributions.**

We value all levels of contribution and want to encourage everyone, regardless of skill level or time available. What matters is being reasonable and meaningful about what you can deliver:

- **Start small and iterate** – Better to do smaller tasks piece by piece than take too much and leave it unfinished. Small contributions add up over time.
- **Break work into steps** – This allows others to take over and continue if needed. It also makes your work more approachable for reviewers.
- **Avoid abandoned PRs** – Forked PRs are difficult to carry over except by maintainers, creating significant burden. If you can't complete a PR, let us know.
- **Be meaningful and reasonable** – Contribute what you can realistically complete. Even small improvements make a difference.

We don't expect perfection. We expect genuine effort. If you're unsure about something, ask! The community is here to help.

## 🌿 Branch Naming Convention

Follow this pattern to keep the repository organized:

```
{type}/{issue-number}-short-description
```

| Type        | Use for                                            |
| :---------- | :------------------------------------------------- |
| `fix/`      | Bug fixes — e.g., `fix/123-warning-crash`          |
| `feat/`     | New features — e.g., `feat/45-class-deprecation`   |
| `docs/`     | Documentation changes — e.g., `docs/update-readme` |
| `refactor/` | Code restructuring without behavior change         |
| `test/`     | Test additions or improvements                     |
| `chore/`    | Maintenance tasks — dependency updates, CI tweaks  |

> [!TIP]
> Always include the issue number when one exists. Without an issue, use a descriptive name: `fix/typo-in-readme`.

## 🚀 Quick Start

```bash
# 1. Fork the repository

# 2. Clone your fork
git clone https://github.com/YOUR-USERNAME/REPO-NAME.git

# 3. Create a feature branch
git checkout -b feature/amazing-feature

# 4. Make your changes

# 5. Stage and commit your changes
git status      # Check which files have been changed
git add -A      # Stage all modified and new files
git commit -m "Add amazing feature"  # Commit the staged changes

# 6. Push to your fork
git push origin feature/amazing-feature

# 7. Open a Pull Request
```

______________________________________________________________________

<div align="center">

**Questions about security?** Contact the project maintainers privately.

Made with 💙 by the Borda et al.

</div>
