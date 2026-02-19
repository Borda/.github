> [!IMPORTANT]
> **Local-only file.** GitHub Copilot only reads `copilot-instructions.md` from the repository it is actively working in — it is **not** automatically applied to other repositories in the organization. To use these instructions in a new project, copy this file into your project's `.github/` directory or fork this repository as a starting point.

# GitHub Copilot Instructions

You are assisting with a **Python project** (ML/AI research or data science). Follow these instructions when generating code, reviewing PRs, and answering questions. Trust these instructions and only search the codebase if something here is incomplete or appears incorrect.

Read `README.md` for project-specific setup. Check `pyproject.toml` for dependencies and tool configuration. The local `CONTRIBUTING.md` overrides these instructions where they conflict.

---

## Project Context

- **Language**: Python 3.10+
- **Linting / formatting**: `ruff` (style, isort, security via `--select S`), enforced through `pre-commit`
- **Testing**: `pytest` + doctests
- **Docstrings**: Google style
- **Packaging**: `pyproject.toml` (`pip` / `uv`)

---

## Coding Conventions

### Python

- Add **type hints** to all new functions and methods.
- Follow **PEP 8**: `snake_case` for functions/variables, `PascalCase` for classes.
- Import order: standard library → third-party → local.
- Prefer explicit over implicit — no magic values, no silent fallbacks.
- Clarity over cleverness: write code that is easy to debug, even if slightly more verbose.

### Docstrings (Google style)

```python
def compute_mean(data: list[float], scale: float = 1.0) -> float:
    """Compute the scaled mean of a dataset.

    Args:
        data: Input values. Must be non-empty.
        scale: Multiplier applied to the result.

    Returns:
        Scaled mean value.

    Raises:
        ValueError: If data is empty.

    Examples:
        >>> compute_mean([1.0, 2.0, 3.0])
        2.0
        >>> compute_mean([1.0, 2.0, 3.0], scale=2.0)
        4.0
    """
```

### Testing

- Write tests **before** fixing bugs or implementing features (TDD).
- Use **doctests** in docstrings for simple input/output examples; use `pytest` for complex scenarios.
- Cover edge cases: `None`, empty inputs (`[]`, `""`), zero/negative values, boundary conditions.
- Assertions must be specific — "no exception raised" is not a sufficient test.

### Error Handling

- **Fail fast** — raise exceptions early with contextual messages (include input values and expected vs. actual).
- Never return magic error codes; never silently swallow exceptions.
- Log or re-raise every caught exception.

### Security

- Never commit `.env` files, API keys, or credentials.
- Validate and sanitize all external input (CLI args, file uploads, API responses).
- Use `ruff --select S` for security linting.

### ML / AI Research

- **Reproducibility**: use fixed random seeds; pin dataset versions and model configs.
- **Data validation**: assert tensor/array shapes, dtypes, and value ranges before processing.
- **Lazy loading**: prefer deferred imports and on-demand computation for large models or datasets.
- **Experiment tracking**: log hyperparameters, metrics, and environment details for every run.
- **Performance**: profile before optimizing; flag O(n²) complexity in hot paths; prefer NumPy vectorization over Python loops.

---

## PR Review Guidelines

When reviewing a pull request, always follow this structured format.

### 1. Overall Recommendation

Open with a clear status and a one-sentence justification:

- 🟢 **Approve** — Ready to merge as-is
- 🟡 **Minor Suggestions** — Non-blocking improvements recommended
- 🟠 **Request Changes** — Issues must be addressed before merge
- 🔴 **Block** — Critical problems require major rework

Example:
```
🟠 Request Changes — Missing unit tests for `DataProcessor` and docstrings not in Google style.
See inline comments for specifics.
```

### 2. PR Completeness Checklist

Mark each item: ✅ Complete / ⚠️ Incomplete / ❌ Missing / 🔵 N/A

- [ ] Clear description of what changed and why
- [ ] Type of change noted (bug fix, feature, refactor, docs…)
- [ ] Linked to a related issue
- [ ] Tests added or updated (unit tests, edge cases)
- [ ] Google-style docstrings for all new/changed public APIs
- [ ] No secrets or credentials introduced
- [ ] Linting passes (`ruff`, `pre-commit`)
- [ ] Changelog / docs entry for user-facing changes (if applicable)

Call out missing items explicitly with links to relevant inline comments.

### 3. Quality Scoring (n/5)

Score three dimensions on a **1–5 scale** with a brief justification:

| Score | Meaning |
| :-- | :-- |
| 5/5 🟢 | Excellent — no issues |
| 4/5 🟢 | Good — minor improvements possible |
| 3/5 🟡 | Adequate — some issues to address |
| 2/5 🟠 | Needs Work — multiple problems |
| 1/5 🔴 | Poor / Missing — significant rework required |

**Code Quality** — correctness, Python best practices, project conventions, type hints, naming.

**Testing Quality** — edge cases covered, assertions specific, regression tests present, realistic scenarios.

**Documentation Quality** — docstrings complete, parameters and exceptions documented, usage examples present.

Use **GitHub inline comments with `suggestion` blocks** for concrete code-level feedback; reference those permalinks in the summary.

### 4. Risk Assessment

Flag risks explicitly with a severity score (1–5):

- **Breaking changes** — API signature changes, removed features; must include migration notes.
- **Performance** — O(n²) loops, memory-heavy operations on large arrays; suggest vectorization.
- **Security** — unvalidated input, credential exposure, unsafe deserialization.
- **Compatibility** — new Python version requirements, new heavy dependencies, platform-specific code.

### 5. Review Summary Template

```markdown
## Review Summary

### Recommendation
[emoji] [Status] — [One-sentence justification]

### PR Completeness
- ✅ [items complete]
- ❌ [items missing]

### Quality Scores
- Code: n/5 [emoji] — [reason]
- Testing: n/5 [emoji] — [reason]
- Documentation: n/5 [emoji] — [reason]

### Risk: n/5 [emoji] — [brief description]

### Must Fix
1. [Specific issue with link to inline comment]

### Suggestions (non-blocking)
1. [Optional improvement with link to inline suggestion]

### Next Steps
1. [Clear action item for the author]
```

### 6. Review Best Practices

**Do:**
- Use GitHub inline comments and `suggestion` blocks directly on code; reference their permalinks in the summary.
- Distinguish blocking issues from nice-to-haves.
- Explain *why* something is a problem, not just *what* is wrong.
- Acknowledge good work and clever solutions.
- Defer style nitpicks to automated tools (`ruff`, `pre-commit`).

**Don't:**
- Give vague feedback like "improve code quality."
- Assume the author knows project conventions — spell it out.
- Let perfect be the enemy of good: minor issues shouldn't block useful PRs.
- Focus only on problems — recognize what's working well.
