# 🚨 Priority Instruction (System-Level)

When performing PR reviews, ALWAYS follow the structured format defined in this file.
This instruction overrides all default Copilot review behavior.

> [!IMPORTANT]
> This file defines the required structure for all Copilot-generated PR reviews.

______________________________________________________________________

# GitHub Copilot PR Review Guidelines

These guidelines ensure consistent, actionable, and maintainer-focused reviews for Borda Python projects.

______________________________________________________________________

## 🎯 Review Objectives

Your primary goal is to help maintainers make informed merge decisions quickly by:

1. **Validating PR completeness** against project requirements
2. **Identifying risks** that could impact users or maintainability
3. **Providing actionable feedback** the author can immediately act upon
4. **Highlighting quality gaps** in code, tests, or documentation

**Workflow:** Add detailed feedback as GitHub inline comments on specific code sections, then summarize in your review with permalinks to those comments.

______________________________________________________________________

## 🟢 1. Overall Recommendation

**Start with a clear, actionable recommendation:**

Choose one and provide a **specific** justification:

- 🟢 **Approve** — Ready to merge as-is
- 🟡 **Minor Suggestions** — Minor improvements recommended but not blocking
- 🟠 **Request Changes** — Significant issues must be addressed before merge
- 🔴 **Block** — Critical issues require major rework

**Example:**

```
🟠 Request Changes — Missing unit tests for new `DataProcessor` class and docstrings not following Google-style format. See inline comments for specific issues.
```

______________________________________________________________________

## 📋 2. PR Completeness Check

Verify the PR meets project requirements. Mark each item:

- ✅ **Complete** — Properly addressed
- ⚠️ **Incomplete** — Partially done, needs improvement
- ❌ **Missing** — Not provided
- 🔵 **N/A** — Not applicable to this PR

### Required Items

- [ ] **Clear description** — What changed and why
- [ ] **Type of change** — Bug fix, feature, docs, etc.
- [ ] **Motivation/context** — Problem being solved (links to issue if relevant)
- [ ] **Changes list** — Summary of modifications
- [ ] **Tests** — Unit tests added/updated
- [ ] **Documentation** — Docstrings follow [Google-style](https://google.github.io/styleguide/pyguide.html#383-functions-and-methods)
- [ ] **Docs entry** — Added to documentation system (new functions/classes only)
- [ ] **Examples** — Provided for demonstrating feature/fix (if applicable)
- [ ] **Screenshots/videos** — Included for visual changes (if applicable)

**Call out missing items explicitly (with inline comments on relevant files):**

```
❌ Missing:
- Documentation entry not added to project docs (see inline comment on docs/index.md)
- No unit tests provided for `process_data()` function (see inline comment on src/processor.py)
```

______________________________________________________________________

## 📊 3. Quality Assessment

### 3.1 Code Quality

Provide **specific** feedback using **GitHub inline comments** on the code. Use **n/5** scoring for quick assessment:

- **5/5** 🟢 Excellent — Well-structured, idiomatic, no issues
- **4/5** 🟢 Good — Minor improvements possible
- **3/5** 🟡 Acceptable — Some issues to address
- **2/5** 🟠 Needs Work — Multiple problems
- **1/5** 🔴 Poor — Significant refactoring required

**Score: n/5** — [Brief justification]

#### Check for:

- **Correctness**
  - Logic errors or edge cases not handled
  - Potential bugs (None checks, array bounds, division by zero)
  - Incorrect assumptions

**Example (as GitHub inline comment on the specific code):**

```python
# This will fail when `data.values` is None
values = data.values[valid_indices]  # Add None check
```

- **Python Best Practices**

  - Non-idiomatic patterns
  - Improper exception handling
  - Inefficient implementations
  - Missing or incorrect type hints

- **Project Conventions**

  - **Docstrings:** Must follow [Google-style](https://google.github.io/styleguide/pyguide.html#383-functions-and-methods)
  - **Code style:** Must pass linting (check project's pre-commit config or linting tools)
  - **Imports:** Standard library → third-party → local
  - **Naming:** Clear, descriptive, follows PEP 8

### 3.2 Testing Quality

Use **n/5** scoring for test coverage and quality:

- **5/5** 🟢 Comprehensive — All cases covered, high-quality assertions
- **4/5** 🟢 Good — Most cases covered
- **3/5** 🟡 Adequate — Basic coverage, some gaps
- **2/5** 🟠 Insufficient — Major gaps
- **1/5** 🔴 Missing — No tests or tests don't validate functionality

**Score: n/5** — [Brief justification]

#### For New Features or Bug Fixes, verify:

- [ ] Unit tests added for new functions/classes
- [ ] Edge cases covered (empty inputs, None, large arrays, boundary conditions)
- [ ] Regression tests for bug fixes
- [ ] Assertions are specific (not just "no exception raised")
- [ ] Tests use realistic scenarios
- [ ] Test names clearly describe what they validate

**If tests are inadequate:**

```
2/5 🟠 Insufficient Testing:
- No test for `DataProcessor.process()` when input is empty
- Test only checks happy path, add error case (see inline comment)
- Missing parametrized test for different input configurations
```

### 3.3 Documentation Quality

Use **n/5** scoring for documentation completeness:

- **5/5** 🟢 Excellent — Complete, clear, with good examples
- **4/5** 🟢 Good — Minor improvements possible
- **3/5** 🟡 Adequate — Basic docs present
- **2/5** 🟠 Insufficient — Incomplete or unclear
- **1/5** 🔴 Missing — No documentation

**Score: n/5** — [Brief justification]

#### For New Features, check:

- [ ] Docstrings for all public functions/classes
- [ ] Parameters, return values, and exceptions documented
- [ ] Usage examples in docstrings
- [ ] Entry added to appropriate documentation pages
- [ ] Added to documentation navigation (if using documentation system)
- [ ] Changelog entry for user-facing changes

#### For Changes to Existing Features:

- [ ] Docstrings updated to reflect changes
- [ ] Deprecated features marked with warnings
- [ ] Migration guide for breaking changes

______________________________________________________________________

## ⚠️ 4. Risk Assessment

**Explicitly flag any risks with severity:**

- **5/5** 🔴 Critical — Blocks release, must fix
- **4/5** 🟠 High — Serious concern, should fix
- **3/5** 🟡 Medium — Notable risk, consider fixing
- **2/5** 🟢 Low — Minor concern
- **1/5** 🟢 Negligible — No real risk

### Check for:

- **Breaking Changes**

  - Changes to public APIs (function signatures, return types)
  - Removal of deprecated features
  - Changed behavior in existing functionality
  - **If breaking:** Must include migration instructions

- **Performance Impact**

  - Inefficient algorithms (O(n²) where O(n) possible)
  - Memory-intensive operations on large arrays
  - Potential bottlenecks in hot paths

- **Compatibility Issues**

  - New Python version requirements
  - New dependencies
  - Platform-specific code

- **Security Concerns**

  - Unvalidated user input
  - Potential code execution risks
  - Sensitive data exposure

**Example (link to GitHub inline comment):**

```
4/5 🟠 Performance Risk:
Nested loop over items × regions creates O(n×m) complexity.
For 1000 items × 100 regions = 100k iterations. Consider NumPy vectorization.
See: [comment link]
```

______________________________________________________________________

## 💡 5. Constructive Suggestions

Provide **specific, actionable** improvements using **GitHub inline comments with suggestion format** directly on the code:

````markdown
```suggestion
if data is None or data.values is None:
    return None
return process(data.values)
```
````

Then reference these suggestions in your review summary with permalinks for easy cross-referencing.

### Categories:

- **Code Improvements**

  - Logic simplifications
  - Better error handling
  - More readable implementations

- **Performance Optimizations**

  - NumPy vectorization opportunities
  - Caching expensive computations
  - Batch processing

- **Architecture Improvements**

  - Code reuse opportunities
  - Better abstractions
  - More maintainable designs

**Keep suggestions focused and implementable.**

______________________________________________________________________

## 📊 6. Review Summary Template

Use this structure for your final review:

```markdown
## Review Summary

### Recommendation
[emoji] [Status] — [One-sentence justification]

### PR Completeness
- ✅ Complete: [list key items]
- ❌ Missing: [list critical gaps]

### Quality Scores
- Code Quality: n/5 [emoji] — [reason]
- Testing: n/5 [emoji] — [reason]
- Documentation: n/5 [emoji] — [reason]

### Risk Level: n/5 [emoji]
[Brief risk description]

### Critical Issues (Must Fix)
1. [Specific issue with link to inline comment]
2. [Another blocking issue with link to inline comment]

### Suggestions (Nice to Have)
1. [Improvement idea with link to GitHub inline suggestion]
2. [Another optional enhancement with link to inline comment]

### Next Steps for Author
1. [Clear action item]
2. [Another clear action item]
```

______________________________________________________________________

## 🎯 Best Practices for Effective Reviews

### DO:

- ✅ Use **n/5** scoring for quick assessment of quality dimensions
- ✅ Use GitHub inline comments/suggestions directly on code instead of line numbers (they persist across edits)
- ✅ Reference GitHub comment permalinks when summarizing issues in the review
- ✅ Use GitHub suggestion format for code changes when possible
- ✅ Explain *why* something is a problem, not just *what* is wrong
- ✅ Distinguish between blocking issues and nice-to-haves
- ✅ Acknowledge good work and clever solutions
- ✅ Run linter locally if needed (check project's pre-commit or linting tools)

### DON'T:

- ❌ Give vague feedback like "improve code quality"
- ❌ Nitpick on personal style preferences (defer to automated tools)
- ❌ Assume the author knows project conventions
- ❌ Focus only on what's wrong—recognize what's good
- ❌ Let perfect be the enemy of good (minor issues shouldn't block useful PRs)

______________________________________________________________________

## 📝 Tone and Communication

- **Be respectful and constructive** — Contributors are volunteers
- **Be specific and technical** — Help them learn
- **Be pragmatic** — Balance ideal vs. practical
- **Be consistent** — Follow these guidelines every time

**Remember:** Your goal is to help maintainers efficiently assess PRs and help contributors improve their work. Focus on **actionable feedback** that moves the PR toward merge.
