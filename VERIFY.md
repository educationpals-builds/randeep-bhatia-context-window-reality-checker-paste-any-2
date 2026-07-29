# VERIFY.md

How a stranger confirms this checker works as claimed.

---

## Verification Protocol

### Step 1: Open the checker

Load the context-checker from `blueprints/context-checker.md` into any chat interface.

### Step 2: Paste the seeded model-card claim

Use this exact input (the first seeded claim from `data/seeded-claims.md`):

```
/verify

"RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work."
```

### Step 3: Confirm the refusal behavior

The checker **must refuse to score** before the job is stated.

Expected behavior:
- The checker does not produce dial ratings
- The checker asks what retrieval task the context window must actually perform
- The checker will not proceed until the user specifies the job in their documents

If the checker scores the claim without asking for the job first, verification fails.

### Step 4: Confirm the missing-artifact detection

Once you provide a job, the checker must name the **missing recall-by-depth curve** as a gap in the claim's evidence.

The claim provides no data showing retrieval accuracy at different positions within the context window. The checker should flag this absence when evaluating the `how_relevance_was_measured` dial.

---

## What passes

1. Checker refuses to score a claim pasted without a job statement
2. Checker prompts for the specific retrieval task
3. After job is provided, checker names the missing recall-by-depth curve in its assessment

## What fails

- Checker scores immediately without asking for the job
- Checker accepts "answer questions about our docs" as a sufficient job statement
- Checker does not mention the absent recall-by-depth evidence

---

## Source files referenced

- Seeded claim: `data/seeded-claims.md`
- Checker spec: `blueprints/context-checker.md`
- Dial definitions: `METHOD.md`
