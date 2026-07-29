# Seeded Claims — Calibration Record

This file contains the two seeded claims used to calibrate the context-window reality checker, along with the advisor's dial strips and the builder's drift ruling.

---

## Seeded Claim 1: The Worked Example

**Claim text:**
"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

**Source:** LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

**Stakes:** Your reply decides whether next quarter's retrieval roadmap survives review

**Deadline:** Before Thursday's roadmap review

### Advisor Dial Strip — Claim 1

| Dial | Advisor Score | Notes |
|------|---------------|-------|
| what_it_must_find | 2 | Task definition incomplete |
| what_the_context_holds | 2 | Haystack composition unspecified |
| how_relevance_was_measured | 2 | No recall-by-depth curve shown |
| where_attention_spreads | 3 | Attention distribution claim made without evidence |
| what_reaches_the_answer | 2 | No verification that retrieved content reached output |

---

## Seeded Claim 2: Model Card Benchmark

**Claim text:**
"Our model achieves 99.1% accuracy on the needle-in-a-haystack benchmark across all context lengths up to 1M tokens."

**Source:** Model card from a major long-context provider

**Stakes:** Determines whether to adopt this model for production document retrieval

**Deadline:** Before architecture decision next sprint

### Advisor Dial Strip — Claim 2

| Dial | Advisor Score | Notes |
|------|---------------|-------|
| what_it_must_find | 1 | Needle task trivial compared to real retrieval |
| what_the_context_holds | 1 | Synthetic haystack, no distractor clauses |
| how_relevance_was_measured | 2 | Single-needle recall only |
| where_attention_spreads | 2 | No attention distribution data |
| what_reaches_the_answer | 1 | No output-level verification |

---

## Builder's Drift Ruling

Must fetch all the info neededm Must fetch all the info needed

---

## Calibration Notes

- Weakest dial across both seeded claims: **what_it_must_find**
- These seeded claims establish the baseline for how the checker should respond to long-context marketing claims
- The advisor's scores on these claims define the calibration standard for future runs
