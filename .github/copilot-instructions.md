> [!IMPORTANT]
> **Local-only file.** GitHub Copilot only reads `copilot-instructions.md` from the repository it is actively working in — it is **not** automatically applied to other repositories in the organization. To use these instructions in a new project, copy this file into your project's `.github/` directory or fork this repository as a starting point.

# GitHub Copilot Instructions

You are assisting with a **Python project** in the Borda organization (typically ML/AI research or data science). Follow these instructions for code generation, Q&A, and PR reviews.

**Trust these instructions.** Only search the codebase if something here seems incomplete or incorrect for the specific project.

---

## Project Context

Read `README.md` for project-specific setup. Check `pyproject.toml` for tool configuration — **it overrides this file where they conflict.**

> [!WARNING]
> **Config files are the source of truth.** If `pyproject.toml` or `.pre-commit-config.yaml` contradict any documentation, trust the config and flag the mismatch.

**If `.github/` docs are absent** (e.g., freshly forked repo), check for a fork with `gh repo view --json parent` and load defaults from upstream. For Borda projects:

- `https://raw.githubusercontent.com/Borda/.github/main/.github/CONTRIBUTING.md`
- `https://raw.githubusercontent.com/Borda/.github/main/AGENTS.md`

**Typical stack:** Python 3.10+, `ruff` (linting + isort + security via `--select S`), `mypy`, `pytest` + doctests, `pre-commit`, `pyproject.toml`.

Local `CONTRIBUTING.md` overrides these instructions where they conflict.

---

## Coding Conventions

### Python

- **Type hints** on all new functions and methods (align with `python_requires` in `pyproject.toml`).
- **PEP 8**: `snake_case` functions/variables, `PascalCase` classes.
- **Imports**: standard library → third-party → local.
- Prefer explicit over implicit — no magic values, no silent fallbacks.

### Docstrings (Google style)

Sections: `Summary`, `Args`, `Returns`, `Raises`, `Examples` (with executable `>>>` doctests). See [CONTRIBUTING.md: Documentation](CONTRIBUTING.md#documentation) for a full example.

### Testing

- Write tests **before** fixing bugs or implementing features (TDD).
- Use **doctests** for simple input/output examples; use `pytest` for complex scenarios.
- Cover edge cases: `None`, empty inputs, zero/negative values, boundary conditions.
- Assertions must be specific — "no exception raised" is not a sufficient test.

### Error Handling

- **Fail fast** — raise exceptions early with contextual messages (include input values).
- Never return magic error codes; never silently swallow exceptions.

### Security

- Never commit `.env` files, API keys, or credentials.
- Validate and sanitize all external input (CLI args, file uploads, API responses).

### ML / AI Research

- **Reproducibility**: fixed random seeds; pin dataset versions and model configs.
- **Data validation**: assert shapes, dtypes, and value ranges before processing.
- **Lazy loading**: deferred imports and on-demand computation for large models/datasets.
- **Experiment tracking**: log hyperparameters, metrics, and environment for every run.
- **Performance**: profile before optimizing; flag O(n²) complexity; prefer vectorization.

---

## PR Reviews

When reviewing a PR, use the structured format defined in [CONTRIBUTING.md — Reviewing PRs](CONTRIBUTING.md#reviewing-prs).

Quick reference:

1. **Recommendation**: 🟢 Approve / 🟡 Minor Suggestions / 🟠 Request Changes / 🔴 Block — with a one-sentence justification.
2. **Completeness**: description, linked issue, tests, docstrings, no secrets, CI passing.
3. **Quality scores** (n/5): Code, Testing, Documentation.
4. **Risk assessment**: breaking changes, performance, security, compatibility.
5. **Summary** using the template in [CONTRIBUTING.md](CONTRIBUTING.md#reviewing-prs).

Use GitHub inline `suggestion` blocks for code fixes; reference their permalinks in the summary. Distinguish blocking issues from nice-to-haves.

---

## Reference

- **Contribution workflow** → [CONTRIBUTING.md](CONTRIBUTING.md)
- **Development standards** → [CONTRIBUTING.md: Development Standards](CONTRIBUTING.md#-development-standards)
- **PR review format** → [CONTRIBUTING.md: Reviewing PRs](CONTRIBUTING.md#reviewing-prs)
- **Branch naming** → [CONTRIBUTING.md: Branch Naming](CONTRIBUTING.md#-branch-naming-convention)
- **Agent behavioral rules** → [AGENTS.md](../AGENTS.md)
- **Security** → [SECURITY.md](SECURITY.md)
