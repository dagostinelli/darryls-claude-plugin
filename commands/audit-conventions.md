# Audit Conventions

Use subagents (the Agent tool) to parallelize this work where possible.

If the project has a `CONVENTIONS.md` file, audit the codebase against it.

If there's no `CONVENTIONS.md` file, stop.

The file could be in a subdirectory, so search for it first.

IMPORTANT: The file might be a symlink. If Glob doesn't find it, use `find -L . -name "CONVENTIONS.md"` or check `docs/CONVENTIONS.md` directly — symlinks are common.

If there is an `ARCHITECTURE.md` file, use it to help you make smart recommendations for this project.
