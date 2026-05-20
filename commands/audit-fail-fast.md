# Fail-Fast Audit

Use subagents (the Agent tool) to parallelize this work where possible.

Use the `fail-fast-auditor` agent to audit the codebase for exception swallowing, silent failures, and defensive coding patterns that mask errors.

Focus on identifying:
- Catch blocks that swallow exceptions without re-throwing
- Default/fallback values that hide failures
- Error-to-friendly-message conversions that obscure underlying bugs
- Empty catch blocks or generic exception handlers
- Logging errors without propagating them

Enforce the 'fail fast' philosophy: errors should surface immediately rather than be hidden by defensive code.

If there are a CONVENTIONS.md and/or an ARCHITECTURE.md file, use them to help you make smart recommendations for this project.
