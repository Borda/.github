# 🏠 Borda's Default GitHub Configuration

[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/Borda/.github/main.svg)](https://results.pre-commit.ci/latest/github/Borda/.github/main)

> 💡 **One configuration to rule them all** — Shared defaults for all Borda repositories.

This repository contains **organization-wide default configurations** for all Borda GitHub projects. These files are automatically inherited by any repository that doesn't define its own versions, reducing duplication and ensuring consistency across the organization.

## 🎯 Purpose

Managing community health files across multiple repositories can be tedious and error-prone. This `.github` repository solves that by providing:

- **Centralized defaults** — Define once, apply everywhere
- **Consistent contributor experience** — Generalized guidelines, templates, and expectations across all projects
- **Reduced maintenance** — Update one file to affect all repositories
- **Quick project bootstrapping** — New repositories immediately inherit best practices

## 📦 What's Included

| File                                                   | Description |
|--------------------------------------------------------|-------------|
| [`CONTRIBUTING.md`](CONTRIBUTING.md)                   | Guidelines for contributing to any Borda project |
| [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md)             | Community standards and enforcement ladder |
| [`AGENTS.md`](AGENTS.md)                               | AI agent configuration and engineering standards |
| [`PULL_REQUEST_TEMPLATE.md`](PULL_REQUEST_TEMPLATE.md) | Default PR template with checklist |
| [`ISSUE_TEMPLATE/...`](ISSUE_TEMPLATE/)                | Bug report and feature request templates |

## 🔄 How GitHub Inheritance Works

GitHub automatically uses files from this `.github` repository as **fallback defaults** for any repository in the organization that doesn't have its own version. This is built into GitHub's [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) feature.

```
┌─────────────────────────────────────────────────────────────────┐
│                     Borda Organization                          │
│                                                                 │
│  ┌──────────────┐        ┌──────────────┐                       │
│  │  .github     │        │  project-A   │                       │
│  │  (this repo) │        │              │                       │
│  │              │        │  No local    │  ──► Uses defaults    │
│  │ CONTRIBUTING │───────►│  overrides   │      from .github     │
│  │ CODE_OF_COND │        │              │                       │
│  │ AGENTS.md    │        └──────────────┘                       │
│  │ ISSUE_TEMPL  │                                               │
│  └──────────────┘        ┌──────────────┐                       │
│         │                │  project-B   │                       │
│         │                │              │                       │
│         │                │  Has local   │  ──► Local file wins  │
│         └───────────────►│  CONTRIBUTING│      (override)       │
│                          │              │                       │
│                          └──────────────┘                       │
└─────────────────────────────────────────────────────────────────┘
```

### Key Behaviors

1. **Automatic fallback**: If a repo doesn't have `CONTRIBUTING.md`, GitHub shows the one from `.github`
2. **Local wins**: A project-specific file **always overrides** the default
3. **Partial override**: Override only what you need — other defaults remain active
4. **Transparent to users**: Contributors see the files seamlessly, regardless of source

## 🎯 When to Use Defaults vs. Override

### ✅ Use the Defaults When

- Starting a **new project** that follows standard Borda practices
- Your project has **no unique contribution requirements**
- You want to **minimize maintenance** overhead
- The project is **small or experimental**

### 🔧 Override When

- Your project has **language-specific setup** (e.g., Python virtualenv, Rust cargo)
- You need **custom issue templates** (e.g., ML model bug report with GPU info)
- The project has **different branching strategies**
- You need **project-specific security policies**

## 📝 How to Override Configuration

To override any default file, simply create the same file in your repository. GitHub will automatically use your local version instead.

### Example: Custom Contributing Guide

Create `CONTRIBUTING.md` in your repository root:

```markdown
# Contributing to My-Awesome-Project

<!-- Your project-specific guidelines here -->

...
```

### Example: Custom Issue Templates

Create `.github/ISSUE_TEMPLATE/` directory with your templates:

```
your-repo/
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md      # Overrides default
│       ├── feature_request.md # Overrides default
│       └── ...
```

### Example: Override AGENTS.md

For projects with specific AI agent requirements:

```markdown
# Project-Specific Agent Configuration

<!-- Import base rules -->
> This extends the [organization defaults](https://github.com/Borda/.github/blob/main/AGENTS.md)

## Additional Rules for This Project

- Use `poetry` instead of `pip` for dependency management
- Run `make lint` before committing
- GPU tests require the `@pytest.mark.gpu` decorator
```

### Partial Override Strategy

You don't need to duplicate everything. Reference the defaults and add only what's different:

```markdown
# Contributing to ML-Pipeline

Please follow [Borda's general contributing guidelines](https://github.com/Borda/.github/blob/main/CONTRIBUTING.md).

## Additional Setup for This Project

...
```

## 🧠 Understanding AGENTS.md

The [`AGENTS.md`](AGENTS.md) file defines standards for AI coding assistants (GitHub Copilot, Claude, Cursor, etc.) working on Borda projects. It establishes:

- **Agent roles** (SW Engineer, QA Specialist, Squeezer, Doc-Scribe, Mentor-Bot)
- **Documentation protocol** (6-point structure for all public APIs)
- **Testing standards** ("The Borda Standard" for rigorous testing)
- **Security protocols** and **error handling** best practices

This ensures consistent AI-assisted development across all projects.

## 🛠️ Maintenance

This repository is maintained by the Borda organization. Changes here affect **all repositories without local overrides**, so modifications are reviewed carefully.

### Proposing Changes

1. **Open an issue** describing the proposed change
2. **Discuss impact** — changes affect many projects
3. **Submit PR** with clear rationale
4. **Get approval** from organization maintainers

### Versioning Strategy

This repository follows **rolling updates**. All changes are immediately reflected in projects using defaults. For breaking changes:

1. Announcement in discussions/issues
2. Grace period for projects to override if needed
3. Implementation of the change

## 📚 Related Resources

- [GitHub: Creating default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
- [Contributor Covenant](https://www.contributor-covenant.org/) — basis for our Code of Conduct

---

<div align="center">

**Questions?** Open an [issue](https://github.com/Borda/.github/issues) or start a [discussion](https://github.com/Borda/.github/discussions).

Made with 💙 by the Borda team

</div>
