# Explore Subsystem

Research a subsystem and produce or amend a proposal.

## Instructions

The user will name a subsystem. Your job is to explore it deeply and ground the conversation in how this kind of problem is approached elsewhere — what tradeoffs are made, what patterns have proven out in practice.

1. **Gather project context**
   - Search the repo for `CONVENTIONS.md`, `ARCHITECTURE.md`, and `AGENTS.md`. They may live at the root, under `docs/`, or be symlinks.
   - If Glob misses them, fall back to `find -L . -name "CONVENTIONS.md" -o -name "ARCHITECTURE.md" -o -name "AGENTS.md"`.
   - Read whichever exist — they describe the project's conventions, architecture, and build/test workflow.

2. **Understand the current implementation**
   - Find the source files for the named subsystem
   - Read the code and understand the current design, limitations, and any known gaps

3. **Survey existing proposals**
   - Look for a proposals directory in the repo (common locations: `docs/proposals/`, `proposals/`, `rfcs/`, `docs/rfcs/`)
   - If found, read any proposals that touch this subsystem
   - Note what's already been proposed, decided, or deferred

4. **Research and discuss**
   - Compare the current approach to how this problem is solved in well-regarded systems in the same space
   - Identify gaps, weaknesses, or missed opportunities
   - Present your findings to the user and have a conversation
   - Be specific: what is missing, why does it matter, what would it take to fix it

5. **Produce or amend a proposal**
   - If an existing proposal covers this: amend it with new findings. Preserve existing content unless it's wrong.
   - If no proposal covers it: create a new one in the proposals directory you discovered. If none exists, create `docs/proposals/` and put it there.
   - Follow the existing format used in the repo; otherwise use: problem statement, proposed approach, options, tradeoffs, effort.
   - Do NOT phase the proposal yet — that is a separate step.

6. **Summarize** what was found and what was written or changed.
