# Polemic Analysis

Run a three-pass Hegelian dialectic on a topic to sharpen thinking and arrive at a defensible Final Proposal.

Each pass is a triad: **thesis (analysis) → antithesis (polemic) → synthesis (proposal)**. The synthesis of each pass becomes the starting point for the next. The progression across the three syntheses is intentional: **balanced → unbalanced → Final**.

## Pick the topic

- If the user passed an argument to `/polemic-analysis`, that argument IS the topic.
- Otherwise, use the subject of the current conversation. If unclear, ask the user.
- The topic might be code, a design idea, an organizational question, a piece of writing — not always codebase stuff.

## The triad

**Thesis — analysis.** Cold, neutral observation. What's actually there. What disagrees with the previous polemic. The thesis exists to resist confirmation bias; without it, the polemics just compound and the proposal calcifies around the loudest first take.

**Antithesis — polemic.** An aggressive, partisan attack on the current state. No hedging, no "on the other hand." The harshest defensible read. The polemic's job is to be so uncharitable that the synthesis has to answer the strongest possible objection, not a softened one.

**Synthesis — proposal.** Combines thesis and antithesis into a position. The character of the synthesis shifts across the three passes (see below).

## The progression: balanced → unbalanced → Final

The three syntheses are NOT three takes on the same answer. They're a deliberate progression:

- **Pass 1 synthesis is balanced.** Fairly weigh the polemic against the analysis. First-cut proposal. This is a stepping stone — its purpose is to be torn at by pass 2.
- **Pass 2 synthesis is unbalanced.** Commit to one side. State what is best. No "we could also." This sharpens pass 1 by abandoning balance — and that imbalance is exactly what the third analysis cold-reads.
- **Pass 3 synthesis is the Final Proposal.** Principled, committed, owns its imbalance with full conviction. This is the answer.

## The principled stance (shapes the polemics and the Final Proposal)

- Recommend and commit. Don't retreat to "or you could keep the status quo" as a balanced third option unless explicitly asked.
- Default toward the principled move. When pragmatism (YAGNI, "it already works", "smaller diff") and principle (right primitive, right place, coherent layering) point in opposite directions, principle wins.
- Categorize by concept, not by convenience.
- Fold bespoke implementations into generic primitives — don't delete the primitive. The hand-rolled reimplementation is the smell.
- No moral arguments about how the topic was or wasn't shipped. Focus on architecture, correctness, UX, and use-case completeness.

## Output

- **Substantive topic** (codebase decision, design proposal, multi-month work): write to a single file. Derive a sensible filename from the topic (e.g., `<short-topic-slug>-POLEMIC.md`) and confirm with the user. Append each step sequentially — do not create multiple files and do not overwrite content.
- **Lightweight conversational topic**: output to chat. Same nine steps, same triad, just inline.

If unsure, ask.

## The three passes

### Pass 1 — first cut
1. **Thesis** *(analysis, neutral)* — Examine the topic's purpose, current state, supporting material. Identify definite gaps that affect correctness. Ignore speculative ideas.
2. **Antithesis** *(polemic)* — Harshest defensible attack on the current state.
3. **Synthesis** *(balanced proposal)* — Answer "What should we do about it?" Fairly weigh the polemic against the analysis. First cut — meant to be torn at next pass.

### Pass 2 — sharpen
4. **Thesis** *(analysis, neutral)* — Re-examine the topic plus everything from pass 1 with cold eyes. What did the polemic miss? What did the balanced proposal soften too much? Resist defending pass 1.
5. **Antithesis** *(polemic)* — Second partisan attack, grounded in what the new analysis surfaced.
6. **Synthesis** *(unbalanced solution)* — Commit. State what is best. Update the proposal toward the committed position, abandoning the balance of pass 1.

### Pass 3 — commit
7. **Thesis** *(analysis, neutral)* — Final cold pass over everything so far. What still doesn't hang together? What did the unbalanced synthesis over-claim?
8. **Antithesis** *(polemic)* — Final partisan attack.
9. **Synthesis** *(Final Proposal)* — Mark as `## Final Proposal`. Principled, committed, owns its imbalance. Do not hedge with alternatives unless the user explicitly asks. This is the answer.

## Rules

- Each step is its own move in the triad — do not blend thesis and antithesis in the same step.
- Append; never overwrite (file mode).
- One file for the whole analysis (file mode).
