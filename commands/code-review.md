# Code Review

Review recent changes by fanning out to specialized subagents in parallel. Use the Agent tool to launch all of these concurrently — do not run them sequentially.

1. **Architectural review** — Use the `grumpy-architect` agent to review the output of `git diff` for architectural soundness, bugs, and feature implementation quality.
2. **Error handling audit** — Use the `fail-fast-auditor` agent to look for exception swallowing, fallback values that hide bugs, and other defensive patterns that mask failures.
3. **Philosophy & principles** — Use the `philosopher-architect` agent to review against documented engineering principles.
4. **Conventions** — Run `/audit-conventions` to check the code against any `CONVENTIONS.md` in the repo.

Launch all four in parallel. Collect their reports and synthesize a unified review highlighting cross-cutting themes.

If there are a `CONVENTIONS.md` and/or an `ARCHITECTURE.md` file, use them to inform the review.
