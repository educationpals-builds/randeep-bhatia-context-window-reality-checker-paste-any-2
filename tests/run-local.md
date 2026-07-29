# Run-Local Guide

Three ways to run the context-window reality checker's probe board locally.

---

## Rung 1: Manual Paste Protocol

For each probe in `tests/probes.jsonl`, follow this protocol:

1. Open any chat model
2. Paste the probe's `input` field
3. Compare the model's response against the `expected` field
4. Record pass/fail for each targeted dial

### Manual Checklist Format

```
Probe: [probe name]
Input: [paste input here]
Expected: [expected behavior]
Actual: [what you observed]
Result: PASS / FAIL
```

Work through all 8 probes (6 pre-generated + 2 learner probes) and tally results.

---

## Rung 2: Script Runner

Save this runner and execute with your API key in the environment.

```python
#!/usr/bin/env python3
"""
Context-checker probe runner.
Reads tests/probes.jsonl, runs each probe, prints graded grid and gate verdict.
"""
import os
import json
import sys

def load_probes(path="tests/probes.jsonl"):
    probes = []
    with open(path, "r") as f:
        for line in f:
            if line.strip():
                probes.append(json.loads(line))
    return probes

def run_probe(probe, client):
    # Implement your model call here using client
    # Return the model's response text
    pass

def grade(response, expected, invariant):
    # Implement grading logic: check if response meets expected behavior
    # Return True for pass, False for fail
    pass

def main():
    api_key = os.environ.get("API_KEY")
    if not api_key:
        print("Set API_KEY in environment")
        sys.exit(1)
    
    probes = load_probes()
    results = []
    for p in probes:
        resp = run_probe(p, api_key)
        passed = grade(resp, p["expected"], p.get("invariant"))
        results.append({"id": p["id"], "name": p["name"], "passed": passed})
    
    print("\n=== GRADED GRID ===")
    for r in results:
        status = "PASS" if r["passed"] else "FAIL"
        print(f"{r['id']}: {r['name']} — {status}")
    
    passed_count = sum(1 for r in results if r["passed"])
    total = len(results)
    print(f"\n=== GATE VERDICT ===")
    print(f"{passed_count}/{total} probes passed")

if __name__ == "__main__":
    main()
```

Run with:
```bash
export API_KEY="your-key-here"
python run_probes.py
```

---

## Rung 3: Eval Tool / CI Integration

Load `tests/probes.jsonl` into any eval runner so the board re-runs automatically when prompts change.

### Loading into an eval framework

The `probes.jsonl` file uses this schema per line:
```json
{"id": "...", "name": "...", "input": "...", "targets": [...], "expected": "...", "invariant": "..."}
```

Point your eval runner's input path to `tests/probes.jsonl`. Map fields:
- `input` → the prompt sent to the model
- `expected` → the grading criteria
- `targets` → which dials this probe tests
- `invariant` → the behavior that must hold

### CI trigger example

```yaml
# .github/workflows/probe-board.yml
on:
  push:
    paths:
      - 'blueprints/**'
      - 'prompts/**'
jobs:
  run-probes:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: python run_probes.py
        env:
          API_KEY: ${{ secrets.API_KEY }}
```

---

## Diffing Against the EP-Certified Board

After running locally, compare your results to the certified board on the listing:

1. Export your local run as JSON (the script prints a grid; capture it)
2. Fetch the EP-certified board from the listing's verification endpoint
3. Diff probe-by-probe:
   - Same pass/fail status → aligned
   - Different status → investigate: prompt drift, model version, or genuine regression

```bash
diff local-board.json certified-board.json
```

Any divergence on the gate metric triggers re-certification review per `tests/pass-gate.md`.
