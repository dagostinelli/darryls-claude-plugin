# Pipeline

Execute a phased proposal one phase at a time.

The user will provide a proposal file path (e.g. `docs/proposals/JOB_SYSTEM.md`).

## Instructions

1. **Read the proposal**
   - Find and read the specified proposal file
   - Identify all phases and their completion status

2. **Phase the proposal if needed**
   - If the proposal has no phases, break it into ordered, actionable phases and write them back to the file
   - If it's already phased, skip this step

3. **Find the current phase**
   - Identify the next incomplete phase
   - If all phases are complete or deemed no longer worthy, report that and stop

4. **Worthiness check**
   - Is this phase still worth doing? Consider: does it still make sense architecturally? Has anything else changed that makes it redundant or premature?
   - Present your reasoning to the user. If not worthy, mark it as such in the proposal and loop back to step 3.

5. **WBS** — run `/wbs` to decompose this phase into beads

6. **Blitz → review → fix loop**
   - Run `/blitz` to execute all ready beads in parallel
   - Run `/code-review` (which runs all audits internally)
   - If any findings were fixed, go back to `/blitz` and repeat
   - Exit this loop only when `/code-review` comes back clean

7. **Stop for human review**
   - Present a summary of what was built and what the audits found
   - Wait for the user to review and approve before proceeding

8. **Mark phase complete**
   - Update the proposal file to mark the phase complete
   - Close out any remaining open beads for this phase

9. **Loop** — go back to step 3 for the next phase

## Important

- One phase at a time — never start the next phase without human sign-off on the current one
- Bead closure happens inside `/blitz` — confirm with the user after each task
- Check `AGENTS.md` (if present) for build, test, and lint commands specific to this project
