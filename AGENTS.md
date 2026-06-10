> [!IMPORTANT]
> **Local-only file.** Not automatically recognized by GitHub across repos. Copy to apply in new projects.

# Agent Configuration (Borda Organization)

______________________________________________________________________

## 1. Anchoring

Read before acting:

1. **This file** (`AGENTS.md`) — behavioral contract; lowest precedence for code decisions
2. **Default config files**: `pyproject.toml`, `.pre-commit-config.yaml`
3. **`README.md`** — scope, setup, key concepts
4. **`.github/CONTRIBUTING.md`** — coding standards, testing, workflow

> [!WARNING]
> **Config files override docs.** `pyproject.toml` or `.pre-commit-config.yaml` contradicts any `.md` → trust config, flag mismatch.

**No `.github/` docs** (fork or template-derived repo):

1. Run `gh repo view --json parent` to check if it is a fork.
2. If forked, fetch upstream org's defaults — for Borda projects:
   - `https://raw.githubusercontent.com/Borda/.github/main/.github/CONTRIBUTING.md`
   - `https://raw.githubusercontent.com/Borda/.github/main/AGENTS.md`
3. Treat as active guidelines until local override exists.

**Precedence:** `pyproject.toml` > local `.github/` > upstream `.github/` > this file. Repo-scoped vs harness-scoped conflicts → §8.

______________________________________________________________________

## 2. Coding & Documentation Standards

→ [CONTRIBUTING.md — Development Standards](.github/CONTRIBUTING.md#-development-standards) (incl. language adaptation for Python, Rust, JS/TS, Go). Agent-specific additions: §3, §4.

______________________________________________________________________

## 3. AI-Specific Constraints

1. **Hallucination guard** — Never invent paths, names, or configs; verify in codebase first.
2. **Verify output** — Run affected test or import module before declaring done. If unable, state reason explicitly.
3. **Signal confidence** — Surface confidence < 80% with percentage and reason. Structured format defined by agent harness.
4. **Verify when suspicious** — Verify when: (a) result depends on external state, (b) exception caught, (c) "works on my machine" claim, (d) silent success after long op, (e) dev/CI env differs.
5. **Human-in-loop** — Flag for human judgment: architecture changes, security policy, data deletion, new features (see §4 for fix/feat boundary).
6. **Source attribution** — Cite file paths and line numbers when referencing code.
7. **Minimal blast radius** — Prefer reversible changes. Before delete, force-push, or drop: pause and confirm scope.
8. **Logging** — Emit logs for functions with ≥2 branches, I/O, retry loops, caught exceptions.

______________________________________________________________________

## 4. Critical Constraints

**Fix vs feat:** `fix` = corrects broken behavior (test or obvious regression). `feat` = new user-visible capability. `refine` = improves existing without new capability. Uncertain → treat as `feat`, get approval.

Standard contributor rules (secrets, bare `except:`, feature approval, least privilege, security policy) → [CONTRIBUTING.md — Security](.github/CONTRIBUTING.md#security) and [Building Features](.github/CONTRIBUTING.md#-building-features-with-consensus).

**Agent-specific:** confirm → execute → update docs in same PR for structural changes (moves, renames, deletes).

______________________________________________________________________

## 5. Agent Roles

Roles defined in `.github/agents/` (Copilot: `@role-name`) and `foundry:<role>` (Claude Code). All role behaviors apply by default; invoke a specific role to emphasize its focus.

______________________________________________________________________

## 6. Commit & PR Conventions

**Commit format** — conventional commits: `type(scope): detail` ≤50 chars.

Types: `fix`, `feat`, `refactor`, `perf`, `test`, `docs`, `ci`, `chore`, `refine`

```
fix(auth): check token expiry with <=
test(parser): add edge case for empty input
docs(readme): update install command
```

Branch naming → [CONTRIBUTING.md — Branch Naming](.github/CONTRIBUTING.md#-branch-naming-convention).

**PR labels**: `needs-qa`, `needs-docs`, `needs-review`, `needs-perf`

> [!NOTE]
> Labels missing in fork: `gh label create needs-qa --color D93F0B --description "QA review required"` (repeat per label).

One PR = one logical change. TODO/FIXME → [CONTRIBUTING.md: Code Markers](.github/CONTRIBUTING.md#code-markers-todo--fixme). PR review format → [CONTRIBUTING.md — Reviewing PRs](.github/CONTRIBUTING.md#reviewing-prs).

______________________________________________________________________

## 7. Live Document Protocol

AGENTS.md = living behavioral contract. Add rules when unexpected agent behaviors occur; don't wait for patterns to repeat.

1. Unexpected behavior → add concrete rule to relevant section in this file
2. Commit: `docs(agents): <what changed>` — one rule per commit; git log is the change history

Downstream forks: compare local version against upstream; pull non-conflicting updates.

______________________________________________________________________

## 8. Conflict Resolution

When this file conflicts with agent harness config:

- **This file wins** — commit format, branch naming, PR labels, test requirements, docstring style
- **Harness wins** — orchestration, task tracking, output routing, timeouts, structured output formats

______________________________________________________________________

## 9. Debugging Protocol

Never patch symptoms. Symptoms = evidence.

1. **Observe** — collect all failure signals before forming hypothesis
2. **Hypothesize** — name specific mechanism ("config key X missing → Y falls back to Z → symptom")
3. **Confirm** — find direct evidence in code/logs/tests; no evidence = no fix
4. **Fix** — change structural cause; no guard that suppresses symptom without removing cause
5. **Validate** — re-run all original signals; any remaining → root cause incomplete → back to step 2

**Loop bound**: max 3 iterations; stop, report symptoms, ask maintainer.

**Forbidden**: bare `except` swallowing failures; default-value fallbacks masking missing config; conditional guards hiding broken state.

______________________________________________________________________

## Reference

- [CONTRIBUTING.md](.github/CONTRIBUTING.md) — standards, PR review, branch naming
- [SECURITY.md](.github/SECURITY.md) — security policy
