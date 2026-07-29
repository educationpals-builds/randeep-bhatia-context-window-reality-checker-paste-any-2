# Probe Board

This board contains all 8 probes used to verify the context-window reality checker. Each probe tests a specific dial behavior.

---

## Probe Format

Each probe specifies:
- **Input**: The claim text fed to the checker
- **Target dial(s)**: Which dial(s) the probe is designed to stress
- **Expected behavior**: What the checker should do
- **Result**: Pass/Fail with notes

---

## Pre-Generated Probes (1–6)

### Probe 1: Missing Haystack Composition

| Field | Value |
|-------|-------|
| **ID** | `pregen-01` |
| **Name** | Missing Haystack Composition |
| **Input** | "Our 1M context model achieved 98% accuracy on document QA." |
| **Target** | `what_the_context_holds` |
| **Expected** | Checker flags missing haystack composition; dial scores ≤2 |
| **Result** | — |

### Probe 2: No Recall-by-Depth Curve

| Field | Value |
|-------|-------|
| **ID** | `pregen-02` |
| **Name** | No Recall-by-Depth Curve |
| **Input** | "Long-context retrieval works perfectly across all positions." |
| **Target** | `where_attention_spreads` |
| **Expected** | Checker asks for recall-by-depth data; dial scores ≤2 |
| **Result** | — |

### Probe 3: Vague Task Definition

| Field | Value |
|-------|-------|
| **ID** | `pregen-03` |
| **Name** | Vague Task Definition |
| **Input** | "Just paste your docs and ask questions — it handles everything." |
| **Target** | `what_it_must_find` |
| **Expected** | Checker refuses to score until job is stated; requests specific retrieval task |
| **Result** | — |

### Probe 4: No Output Verification

| Field | Value |
|-------|-------|
| **ID** | `pregen-04` |
| **Name** | No Output Verification |
| **Input** | "The model found the answer in our 500-page contract corpus." |
| **Target** | `what_reaches_the_answer` |
| **Expected** | Checker asks whether answer actually used retrieved content; dial scores ≤2 |
| **Result** | — |

### Probe 5: Missing Relevance Measurement

| Field | Value |
|-------|-------|
| **ID** | `pregen-05` |
| **Name** | Missing Relevance Measurement |
| **Input** | "Our benchmark shows the model attends to relevant passages." |
| **Target** | `how_relevance_was_measured` |
| **Expected** | Checker asks for relevance measurement methodology; dial scores ≤2 |
| **Result** | — |

### Probe 6: Complete Claim with Evidence

| Field | Value |
|-------|-------|
| **ID** | `pregen-06` |
| **Name** | Complete Claim with Evidence |
| **Input** | "We tested on 10K contracts with planted clauses at positions 1K, 50K, 200K, 500K tokens. Recall was 94% at 1K, 91% at 50K, 87% at 200K, 71% at 500K. Each answer was verified against source spans." |
| **Target** | All dials |
| **Expected** | Checker scores all dials ≥3; notes the depth-decay pattern |
| **Result** | — |

---

## Learner Probes (7–8)

### Probe 7: Learner Probe A

| Field | Value |
|-------|-------|
| **ID** | `learner-01` |
| **Name** | Learner Probe A |
| **Input** | Must fetch all the info neededm Must fetch all the info needed |
| **Target** | Per learner specification |
| **Expected** | Per learner specification |
| **Result** | — |

### Probe 8: Learner Probe B

| Field | Value |
|-------|-------|
| **ID** | `learner-02` |
| **Name** | Learner Probe B |
| **Input** | Must fetch all the info neededm Must fetch all the info needed |
| **Target** | Per learner specification |
| **Expected** | Per learner specification |
| **Result** | — |

---

## Results Grid

| Probe ID | Name | Target Dial | Expected | Actual | Status |
|----------|------|-------------|----------|--------|--------|
| pregen-01 | Missing Haystack Composition | what_the_context_holds | dial ≤2 | — | — |
| pregen-02 | No Recall-by-Depth Curve | where_attention_spreads | dial ≤2 | — | — |
| pregen-03 | Vague Task Definition | what_it_must_find | refuses until job stated | — | — |
| pregen-04 | No Output Verification | what_reaches_the_answer | dial ≤2 | — | — |
| pregen-05 | Missing Relevance Measurement | how_relevance_was_measured | dial ≤2 | — | — |
| pregen-06 | Complete Claim with Evidence | all | all dials ≥3 | — | — |
| learner-01 | Learner Probe A | per spec | per spec | — | — |
| learner-02 | Learner Probe B | per spec | per spec | — | — |

---

## Board Reading

Must fetch all the info neededm Must fetch all the info needed

---

## Machine-Readable Source

The canonical probe definitions live in `tests/probes.jsonl`. This board renders that file for human review.
