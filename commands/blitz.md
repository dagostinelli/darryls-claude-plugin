Parallelize all ready tasks using git worktrees and subagents to bang them all out in one shot.

## Instructions

1. Verify prerequisites:
   - Confirm we're in a git repository (`git rev-parse --git-dir`)
   - Confirm `bd` is available
   - Confirm the working tree is clean (`git status --porcelain`) — if not, stop and tell the user to commit or stash first

2. Get the current state:
   ```
   bd ready
   bd list
   ```

3. Collect all ready (unblocked) tasks. For each one, run `bd show <id>` to get full details. Present the list to the user and ask:
   - **Which tasks to include** — default is all ready tasks
   - **Base branch** — which branch to create worktrees from (default: current branch)

4. For each selected task, create a git worktree:
   ```
   git worktree add ../<repo-name>-blitz-<bead-id> -b blitz/<bead-id>-<short-title>
   ```
   Use a sanitized version of the task title (lowercase, hyphens, no special chars) for the branch name.

5. **Use subagents to do all the work in parallel.** For each worktree, use the Agent tool to launch a subagent. Each subagent should:
   - Use `EnterWorktree` to enter its assigned worktree directory
   - Read the task details from `bd show <id>`
   - Implement the task fully — code, tests, whatever is needed
   - Run any existing test suite to verify nothing is broken
   - Report back what was done and whether tests pass

   **IMPORTANT**: Launch ALL subagents in parallel using the Agent tool — this is the whole point. Do not wait for one to finish before starting the next. Each subagent works independently in its own worktree so there are no conflicts.

6. As subagents complete, collect their results. For each completed task:
   - Report success/failure and a summary of changes to the user
   - If successful, ask the user if they want to mark it done with `bd close <id>`

7. After all subagents finish, show a summary:
   - Which tasks succeeded vs failed
   - The branches created for each task
   - Suggest next steps: review branches, merge them, run full test suite, etc.

8. Merge all the worktrees into the master branch using rebase/cherry-pick and then remove the worktrees. Do not lose work!

9. Close completed beads, and plan the next batch.

## Important

- Each worktree is an independent copy of the repo — subagents won't conflict with each other
- Do NOT leave work in worktrees — complete the work and bring it all back to the master branch
- Do NOT have extra stuff in the commit message about how the coding assistant helped
- Do NOT push git commits
- If a task is too vague to implement, the subagent should document what it understood and what decisions need to be made, rather than guessing
- If there are more than 5 ready tasks, recommend batching to avoid overwhelming the system — suggest the highest-impact 5 first
- Use `bd show <id>` to get full context for each task before handing it to a subagent

If there are a `CONVENTIONS.md` and/or an `ARCHITECTURE.md` file, use them to help you make smart recommendations for this project.
