# Context-Window Reality Checker

A five-dial framework for evaluating long-context claims before they derail your roadmap.

## How This Checker Was Built

This checker emerged from a real decision: whether to trust a vendor claim that "RAG is dead" and abandon retrieval engineering. Instead of accepting or rejecting the claim on vibes, I ran it through five diagnostic dials that expose what any long-context claim actually demonstrates.

The result is a reusable checker you can paste into any conversation to get a structured read on context-window claims.

## The Worked Example

**The claim:**
> "RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

**Who said it:** LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

**What it decides:** Your reply decides whether next quarter's retrieval roadmap survives review

**Deadline:** Before Thursday's roadmap review

**The job it must do:** Must fetch all the info needed make sure it works.

**Weakest dial:** what_it_must_find

**Verdict:** Must fetch all the info needed, Must fetch all the info needed

See [charter.md](charter.md) for the full five-dial breakdown, flip condition, and the questions sent back.

## Repository Structure

| Path | Purpose |
|------|---------|
| `charter.md` | The full worked example with all five dials scored |
| `blueprints/context-checker.md` | One-paste system instructions for the checker |
| `prompts/context-check-pack.md` | Five standalone prompts, one per dial |
| `METHOD.md` | The SIGHT framework explained |
| `VERIFY.md` | How to verify this checker works |
| `skills/context-advisor.skill.md` | Portable skill file for assistant runtimes |
| `data/seeded-claims.md` | Calibration record with seeded claims |
| `tests/probe-board.md` | All 8 probes with results |
| `tests/pass-gate.md` | The gate this checker must hold |
| `tests/probes.jsonl` | Machine-readable probe export |
| `tests/run-local.md` | Run-anywhere guide |
| `STORY.md` | The builder's story |

## One-Paste Rebuild

To rebuild this checker in any chat interface:

```
You are a context-window claim checker. When someone pastes a long-context claim, you:

1. REFUSE to score until they state the specific retrieval job the context window must perform
2. Run five dials (0-4 each):
   - what_it_must_find: Is the retrieval task specified?
   - what_the_context_holds: Is the haystack composition disclosed?
   - how_relevance_was_measured: Is there a recall-by-depth curve or equivalent?
   - where_attention_spreads: Are distractor patterns documented?
   - what_reaches_the_answer: Does output verification show the answer used retrieved content?
3. Name the weakest dial
4. State your verdict with the cost of being wrong
5. List questions to send back to the claimant

Calibration example — see charter.md in this repository.
```

## License

MIT

<!-- educationpals-build-verified -->
