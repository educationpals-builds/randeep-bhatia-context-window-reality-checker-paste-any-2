# Context-Check Prompt Pack

Five standalone prompts for evaluating long-context claims. Each targets one dial from the five-signal framework. Paste any single prompt into a chat model to run that check independently.

---

## Prompt 1: What It Must Find

```
You are evaluating a long-context claim. Your job is to assess the "what_it_must_find" dial.

The claim being evaluated:
"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

Source: LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

Ask yourself:
1. Does the claim specify what the model must actually locate in the context?
2. Is there a concrete retrieval task named (e.g., "find clause X and link it to clause Y")?
3. Or is the task left vague ("answer questions about docs")?

Score 0–4:
- 0: No task specified at all
- 1: Task implied but not stated
- 2: Task stated but generic
- 3: Task stated with document type but not specific target
- 4: Task names document type AND specific thing to find/link

Output your score and one-sentence reasoning.
```

---

## Prompt 2: What The Context Holds

```
You are evaluating a long-context claim. Your job is to assess the "what_the_context_holds" dial.

The claim being evaluated:
"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

Source: LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

Ask yourself:
1. Does the claim describe what was actually in the test context?
2. Is the haystack composition disclosed (document types, distractor ratio, depth distribution)?
3. Or is "the whole corpus" left undefined?

Score 0–4:
- 0: No description of context contents
- 1: Vague reference ("documents", "corpus")
- 2: Document type named but no composition details
- 3: Composition partially described
- 4: Full haystack spec: types, distractors, depth curve

Output your score and one-sentence reasoning.
```

---

## Prompt 3: How Relevance Was Measured

```
You are evaluating a long-context claim. Your job is to assess the "how_relevance_was_measured" dial.

The claim being evaluated:
"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

Source: LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

Ask yourself:
1. Does the claim explain how "attending equally well" was measured?
2. Is there a recall-by-depth curve or position-sensitivity test?
3. What metric proves the model found the right thing vs. hallucinated?

Score 0–4:
- 0: No measurement method mentioned
- 1: Anecdotal ("it worked")
- 2: Single-point accuracy mentioned
- 3: Multiple positions tested but no curve
- 4: Full recall-by-depth curve with methodology

Output your score and one-sentence reasoning.
```

---

## Prompt 4: Where Attention Spreads

```
You are evaluating a long-context claim. Your job is to assess the "where_attention_spreads" dial.

The claim being evaluated:
"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

Source: LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

Ask yourself:
1. Does the claim provide evidence about attention distribution?
2. Is there data showing attention doesn't decay with position?
3. Or is "attends to everything equally" asserted without proof?

Score 0–4:
- 0: No attention evidence
- 1: Assertion without data
- 2: Indirect evidence (output quality)
- 3: Some attention analysis shown
- 4: Full attention maps or equivalent proof

Output your score and one-sentence reasoning.
```

---

## Prompt 5: What Reaches The Answer

```
You are evaluating a long-context claim. Your job is to assess the "what_reaches_the_answer" dial.

The claim being evaluated:
"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."

Source: LinkedIn post by a long-context vendor's head of product, forwarded by the CEO

Ask yourself:
1. Does the claim verify the answer actually used what was retrieved?
2. Is there a check that the output cites or traces back to source material?
3. Or could the model have answered from parametric knowledge alone?

Score 0–4:
- 0: No verification that answer used context
- 1: Output looked right (no trace)
- 2: Answer mentioned source but no verification
- 3: Some citation checking
- 4: Full provenance trace from answer to source location

Output your score and one-sentence reasoning.
```

---

## Usage

1. Pick the dial most relevant to your current concern
2. Paste that prompt into any chat model
3. Replace the claim text with the claim you're evaluating
4. Review the score and reasoning
5. Repeat for other dials as needed

For the full five-dial check in one pass, see `blueprints/context-checker.md`.
