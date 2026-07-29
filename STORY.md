# What I Built

I built a context-window reality checker — a tool that takes any long-context claim and runs it through five dials before I have to stake a position.

The claim that started this: "RAG is dead. With million-token context windows you paste the whole corpus in and the model attends to everything equally well — retrieval engineering is legacy work." It came from a LinkedIn post by a long-context vendor's head of product, forwarded by the CEO. My reply decides whether next quarter's retrieval roadmap survives review.

## The Probe That Fooled It

From the probe board in `tests/probe-board.md`:

> "Must fetch all the info neededm Must fetch all the info needed"

The checker let this through when it should have flagged the missing specificity. The weakest dial was `what_it_must_find` — the job definition was too vague to score meaningfully.

## The Fix

I tightened the intake rule: the checker now refuses to score any claim until the user states the concrete retrieval task. A job like "Must fetch all the info needed" fails the gate. The checker asks back: what document type, what must be found or linked, what counts as success.

## The Gate It Holds

The pass gate from `tests/pass-gate.md`:

> Must fetch all the info neededm Must fetch all the info needed

## Re-Certification Cadence

Before each roadmap review cycle, I re-run the probe board. If any dial drifts from its expected behavior, I update the calibration in `charter.md` and re-verify.

## The Domain Lesson

Long-context claims sound compelling until you ask what the context actually holds and whether the answer used what was retrieved. The five dials force that question before I commit to a position. The failure on the vague-job probe taught me that the checker is only as good as the job definition I feed it — garbage in, false confidence out.

---

*Verification: see `tests/probe-board.md` for the full board, `tests/pass-gate.md` for the threshold, and `provenance.json` for build lineage.*
