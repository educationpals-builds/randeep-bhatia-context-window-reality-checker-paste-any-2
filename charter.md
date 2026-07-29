# Context-Window Reality Checker — Charter

This document records the full run: the claim under review, the job it must perform, the stakes, the deadline, the five-dial assessment, the verdict, the flip condition, and the questions sent back.

---

## The Pinned Claim

**Claim (verbatim):**

> "RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

**Source:** LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

---

## The Job It Must Do

**What this decides:** Your reply decides whether next quarter's retrieval roadmap survives review

**Deadline:** Before Thursday's roadmap review

**The retrieval task it must actually perform:**

> Must fetch all the info needed make sure it works.

---

## Five-Dial Assessment

| Dial | Score (0–4) | Reason |
|------|-------------|--------|
| what_it_must_find | 2 | The claim does not specify what the model must locate in the corpus |
| what_the_context_holds | 2 | No description of haystack composition or document types |
| how_relevance_was_measured | 2 | No recall-by-depth curve or retrieval metrics disclosed |
| where_attention_spreads | 3 | Claim asserts "attends to everything equally" without evidence |
| what_reaches_the_answer | 2 | No verification that retrieved content actually influenced output |

**Weakest signal:** what_it_must_find

**Test setup shown vs conspicuously missing:**

> Must fetch all the info needed

---

## Verdict

> Must fetch all the info needed, Must fetch all the info needed

---

## Flip Condition

What evidence would change this read:

> Must fetch all the info needed, Must fetch all the info needed

---

## Questions Sent Back

1. Must fetch all the info neededm Must fetch all the info needed
2. Must fetch all the info neededm Must fetch all the info needed
3. Must fetch all the info neededm Must fetch all the info needed

---

*This charter serves as the worked example for the context-window reality checker. See [blueprints/context-checker.md](blueprints/context-checker.md) for the system spec and [METHOD.md](METHOD.md) for the five-dial framework.*
