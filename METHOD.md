# METHOD: The SIGHT Framework

This file defines the five-signal framework for evaluating long-context claims. The acronym **SIGHT** maps each letter to a dial that probes a different failure mode in context-window retrieval.

---

## The SIGHT Acronym

| Letter | Dial Key | What It Probes |
|--------|----------|----------------|
| **S** | `what_it_must_find` | **Specificity of the retrieval task** — Does the claim name what must actually be found, or does it wave at "understanding"? |
| **I** | `what_the_context_holds` | **Inventory of the haystack** — Is the corpus composition disclosed? Distractor density? Document types? |
| **G** | `how_relevance_was_measured` | **Grounding of relevance** — Was there a recall-by-depth curve, or just vibes? |
| **H** | `where_attention_spreads` | **Heat distribution** — Does attention actually reach the target position, or does it pool at boundaries? |
| **T** | `what_reaches_the_answer` | **Throughput to output** — Did the answer demonstrably use what was retrieved, or did it hallucinate a plausible response? |

---

## Mechanism Mapping

Each dial operates like an attention head with its own query, key space, scoring function, and value extraction:

### S — Specificity (`what_it_must_find`)

- **Query**: "What concrete artifact must the model locate?"
- **Keys**: Named document types, clause references, entity links
- **Scoring**: Binary — either the task names a findable thing or it doesn't
- **Softmax weighting**: High weight when task is vague; low weight when task is concrete
- **Values**: The specific retrieval target (e.g., "§7 liability cap linked to §19 carve-out")

### I — Inventory (`what_the_context_holds`)

- **Query**: "What is the haystack made of?"
- **Keys**: Document count, type distribution, distractor ratio, needle placement
- **Scoring**: 0–4 based on disclosure completeness
- **Softmax weighting**: Increases when composition is hidden
- **Values**: Haystack metadata (size, structure, adversarial content)

### G — Grounding (`how_relevance_was_measured`)

- **Query**: "How was retrieval success measured?"
- **Keys**: Recall metrics, depth curves, position-aware accuracy
- **Scoring**: 0–4 based on methodological rigor
- **Softmax weighting**: Peaks when only end-to-end accuracy is reported
- **Values**: The measurement protocol (or its absence)

### H — Heat (`where_attention_spreads`)

- **Query**: "Where does attention actually land?"
- **Keys**: Attention maps, position bias data, boundary pooling evidence
- **Scoring**: 0–4 based on attention distribution evidence
- **Softmax weighting**: High when no attention analysis is provided
- **Values**: Attention pattern data or stated assumptions

### T — Throughput (`what_reaches_the_answer`)

- **Query**: "Did the output use what was found?"
- **Keys**: Citation traces, quote verification, provenance chains
- **Scoring**: 0–4 based on output-to-source linkage
- **Softmax weighting**: Maximum when answer correctness is assumed from retrieval
- **Values**: Evidence that retrieved content reached the generation step

---

## Scoring Protocol

Each dial scores 0–4:

| Score | Meaning |
|-------|---------|
| 0 | No evidence provided |
| 1 | Claim made without support |
| 2 | Partial evidence, critical gaps |
| 3 | Solid evidence, minor gaps |
| 4 | Full disclosure, verifiable |

The **weakest dial decides the verdict**. A claim with four 4s and one 1 is a 1-claim.

---

## Using the Framework

1. **Pin the claim** — Copy the exact text being evaluated
2. **Run all five dials** — Score each 0–4 with a one-line reason
3. **Identify the weakest** — This dial sets your confidence ceiling
4. **Call the verdict** — State your position, the deciding dial, and the cost of being wrong
5. **Write the questions** — Ask for the artifacts that would move the weakest dial

The checker in `blueprints/context-checker.md` implements this protocol conversationally. The prompts in `prompts/context-check-pack.md` let you run each dial standalone.

---

## Why SIGHT

Long-context claims fail in predictable places. Most fail at S — they never name what must be found. Many fail at T — they assume retrieval implies use. The framework forces you to check each failure mode before you trust or dismiss a claim.

The letters exist only in this file. Everywhere else, use the dial keys.
