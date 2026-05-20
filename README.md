# darryls-claude-plugin

A Claude Code plugin bundling the commands and subagents I actually use.

## Install

Inside Claude Code:

```
/plugin marketplace add dagostinelli/darryls-claude-plugin
/plugin install darrylagostinelli@darryls-claude-plugin
```

The first command adds this GitHub repo as a plugin marketplace; the second installs the plugin from it.

## Commands

- `/code-review` — Fan out to specialized reviewer subagents in parallel for a comprehensive review.
- `/audit-conventions` — Audit the codebase against `CONVENTIONS.md` if present.
- `/audit-fail-fast` — Standalone fail-fast audit via the `fail-fast-auditor` agent.
- `/explain` — Explain how the code at the current location/file works and how it fits the larger system.
- `/explore` — Research a subsystem and produce or amend a proposal.
- `/document` — Generate comprehensive code documentation: function docs, complex logic explanations, API/data structure docs.
- `/performance-review` — Analyze code for performance bottlenecks, algorithmic improvements, memory issues, and caching opportunities.
- `/security-review` — OWASP-style security audit: auth, secrets, input validation, error leakage, crypto.
- `/polemic-analysis` — Multi-pass analyze → polemic → propose loop on a topic (argument or current conversation), producing a single Final Proposal file.
- `/grumpy` — Standalone architectural review via the `grumpy-architect` agent.
- `/philosopher` — Standalone principle-based review via the `philosopher-architect` agent.
- `/wbs` — Build a work-breakdown structure in [beads](https://github.com/steveyegge/beads) (`bd`).
- `/blitz` — Parallelize all ready beads across git worktrees + subagents.
- `/pipeline` — Execute a phased proposal one phase at a time: `wbs → blitz → code-review` per phase.

## Subagents

- `grumpy-architect` — Hard-nosed architectural review.
- `fail-fast-auditor` — Catches exception swallowing, silent failures, defensive coding that hides bugs.
- `philosopher-architect` — Reviews against documented engineering principles.

## Requirements

- `/wbs`, `/blitz`, `/pipeline` require the [`bd`](https://github.com/steveyegge/beads) CLI.
- `/blitz` and `/pipeline` use git worktrees — the working tree must be clean before running.
