# Pass Gate

The quality gate this checker must hold before deployment and on every re-certification.

---

## Gate Definition

**Metric, threshold, and re-run cadence:**

Must fetch all the info neededm Must fetch all the info needed

---

## Re-Run Trigger

The gate re-runs when:
- Any prompt in `blueprints/context-checker.md` changes
- New probes are added to `tests/probes.jsonl`
- The calibration record in `data/seeded-claims.md` is updated

---

## Contested-Call Rulings

When the checker and a human evaluator disagree on a dial score, the ruling is recorded here with Atlas's opposing case preserved.

| Probe | Dial | Checker Score | Human Score | Ruling | Atlas's Opposing Case |
|-------|------|---------------|-------------|--------|----------------------|
| — | — | — | — | — | No contested calls recorded in this run |

---

## Verification

To verify this gate holds:
1. Load `tests/probes.jsonl`
2. Run all 8 probes through the checker
3. Compare results against expected behaviors in `tests/probe-board.md`
4. Confirm the metric meets threshold

---

*This gate references `tests/probes.jsonl` as the authoritative probe source.*
