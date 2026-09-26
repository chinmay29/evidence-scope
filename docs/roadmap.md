# Roadmap

**Status: design and repository scaffold only.** Every implementation milestone below remains open.

## 1. Establish feasibility

- [ ] Prepare 20–30 labeled cases from pinned public documentation.
- [ ] Confirm live Jev access and supported judgment contracts.
- [ ] Compare metadata rules, an inexpensive structured-output LLM, and Jev.
- [ ] Review quality, coverage, latency, and cost before committing to the interface.

If rules solve most cases, narrow the semantic gate to the remaining evidence problem. If another judge performs better, preserve that finding rather than designing a benchmark to force a Jev win.

## 2. Build the core

- [ ] Verify source licenses and publish a reproducible corpus manifest.
- [ ] Define passage, scope, decision, and trace contracts.
- [ ] Implement retrieval, metadata eligibility, and the Jev adapter.
- [ ] Implement bounded recovery, explicit abstentions, and citation validation.
- [ ] Test route invariants, scope handling, provider failures, and budgets.

## 3. Build the reference application

- [ ] Connect retrieval, gating, and a fixed answer generator.
- [ ] Build an evidence inspector with visible exclusions and decisions.
- [ ] Provide clearly labeled recorded replay and configured live modes.
- [ ] Add an example integrating caller-supplied passages.

## 4. Evaluate and release

- [ ] Freeze grouped dataset splits and calibration thresholds.
- [ ] Run all four evaluation arms and publish failures with results.
- [ ] Document setup, limitations, measurements, and reproduction steps.
- [ ] Add credential-free CI and a recorded demo runnable from a fresh clone.
- [ ] Publish the first implemented release only after the documented checks pass.

Arbitrary crawling, autonomous execution, multi-tenancy, and multiple framework integrations are outside the first release. See [architecture](architecture.md) and [evaluation](evaluation.md) for the proposed boundaries and acceptance evidence.
