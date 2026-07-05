# Code Review

Review recent changes by fanning out to specialized subagents in parallel. Use the Agent tool to launch all of these concurrently — do not run them sequentially.

1. **Architectural review** — Use the `grumpy-architect` agent to review the output of `git diff` for architectural soundness, bugs, and feature implementation quality.
2. **Error handling audit** — Use the `fail-fast-auditor` agent to look for exception swallowing, fallback values that hide bugs, and other defensive patterns that mask failures.
3. **Philosophy & principles** — Use the `philosopher-architect` agent to review against documented engineering principles.
4. **Conventions** — Run `/darrylagostinelli:audit-conventions` to check the code against any `CONVENTIONS.md` in the repo.
5. **Git history** — Spawn a subagent to run `git log --follow -p` and `git blame` on the modified files. Look for invariants, prior reverts, or comments in the history that the current change may violate or repeat.
6. **Prior review comments** — Spawn a subagent to run `git log --oneline` on the modified files and look for any prior commits that reference a fix or revert of the same area. Flag recurring issues.

Launch all six in parallel. Collect their reports and score each finding on a 0–100 confidence scale (0 = false positive, 100 = certain real issue). Drop anything below 65. Synthesize the survivors into a unified review highlighting cross-cutting themes.

If there are a `CONVENTIONS.md` and/or an `ARCHITECTURE.md` file, use them to inform the review.
