Build a work-breakdown structure and store it in beads (`bd`). Set up, extend, or manage a product by decomposing it into epics, features, and tasks.

## Instructions

1. **Check if beads is initialized** in the current directory:
   ```
   bd list
   ```
   If the command fails or indicates beads is not initialized (e.g., no `.beads` folder exists), ask the user:
   > "Beads doesn't appear to be initialized here. Would you like to initialize it now with `bd init`?"
   - If yes: run `bd init`, then continue to step 3.
   - If no: stop here.

2. **If beads already exist**, show them to the user and ask what they'd like to do:
   - **Add features/tasks** — create new beads under existing features
   - **Create a brand new product** — start fresh (go to step 3)
   - **Update status** — close/reopen beads (`bd close <id>`, `bd reopen <id>`)
   - **Reprioritize** — change priority levels (`bd edit <id> -p <priority>`)
   - **Add dependencies** — wire up new dependency relationships (`bd dep add <blocked> <blocking>`)
   - **Edit details** — update title or description (`bd edit <id> -t "new title"` or `bd edit <id> -d "new desc"`)
   - **Remove tasks** — delete beads that are no longer needed (`bd rm <id>`)

   If adding features to an existing product, skip to step 6 using the existing P0 epic as the parent.
   If managing existing beads, execute the appropriate `bd` commands and skip to step 9.

3. **Check if there's an existing codebase** in the current directory. Look at the project structure — source files, package manifests, READMEs, config files, etc. If there's a substantial codebase already:
   - Explore the codebase to understand its architecture, modules, and major components
   - Read the README, docs, or any planning files if they exist
   - Identify the major functional areas / modules of the project
   - Present a summary to the user: "This looks like a [type] project with these major areas: ..."
   - Ask the user: **What's the current state?** What's done, what's in progress, what's planned?
   - Use their answers to create beads that reflect reality — mark completed work as closed, in-progress work as open, and planned work as open with appropriate dependencies

4. Ask the user for:
   - **Product name** (short, descriptive)
   - **Product description** (one-liner summary)

5. Create a top-level P0 bead as the product epic:
   ```
   bd add -p P0 -t "<product name>" -d "<description>"
   ```

6. Ask the user: **What are the key features or milestones?** If you analyzed the codebase in step 3, propose a breakdown based on what you found and let the user adjust it.

7. For each feature/milestone:
   - Create a P1 bead as a child of the epic
   - Ask the user if this feature should be broken down further into subtasks
   - If yes, create P2 beads for the subtasks
   - If the codebase analysis showed this feature is already done, close it immediately with `bd close <id>`

8. Wire up dependencies using `bd dep add <child> <parent>` where tasks depend on each other. Ask the user about ordering/dependencies between features.

9. After all changes, show the current state:
   ```
   bd list
   bd ready
   ```
   Show the user the full product breakdown and what's actionable now.

10. If there are ready tasks, suggest running `/darrylagostinelli:blitz` to parallelize them.

## Important

- Use `bd add` to create beads (issues/tasks)
- Use `bd dep add <blocked-issue> <blocking-issue>` to set dependencies
- Use `bd dep rm <blocked> <blocking>` to remove dependencies
- Use `bd close <id>` for already-completed work
- Use `bd show <id>` to display details of a specific bead when needed
- Priority levels: P0 (epic), P1 (feature/milestone), P2 (subtask)
- Always show the user the bead IDs after creation so they can reference them
- When analyzing an existing codebase, don't create beads for every file — group by logical feature/module
- Always show before/after state so the user can see what changed
- Confirm destructive operations (close, remove) with the user before executing
