# Evaluation plan

**Status: planned; no benchmark has run and no results are claimed.**

The hypothesis is that a Jev evidence gate can reduce unsupported or incorrectly scoped answers beyond metadata filtering, while preserving useful answer coverage at a competitive total cost. The comparison must allow this hypothesis to fail.

## Comparison arms

| Arm | Purpose |
| --- | --- |
| Retrieval + generation | Ordinary documentation assistant baseline. |
| Retrieval + deterministic metadata rules + generation | Establish what explicit scope handling already solves. |
| Same rules + inexpensive structured-output LLM gate | Test a practical competing semantic judge. |
| Same rules + Jev gate | Measure Jev's incremental contribution. |

Use the same pinned corpus, stated target scope, answer generator, and equivalent retrieval budgets. The two semantic gates will use equivalent decision tasks and recovery policies. Select and pin an inexpensive model with actual structured-output support during implementation.

Run both frozen-bundle evaluation, giving comparable judges identical evidence, and end-to-end evaluation covering retrieval, recovery, generation, and validation. The former isolates decisions; the latter measures user-visible outcomes.

## Dataset and splits

Target approximately 150 manually checked cases across roughly 30 topic/API-change families. Include answerable questions, older-version distractors, mixed-version migration passages, incomplete evidence, unavailable answers, harmless conditional differences, and explicitly labeled synthetic conflicts or hostile source instructions. Keep ordinary cases well represented and report categories separately.

An initial split is 15 families for prompt development, five for calibration, and ten for final testing. Keep all related question variants and source passages in the same family to reduce leakage. Freeze the test set before selecting the final operating point.

Human labels will record scope applicability, semantic sufficiency, conflicts, supporting spans, and material answer facts. Label these separately from routes: the appropriate route also depends on remaining recovery budget. Jev predictions must not become reference labels. Manually audit final answers blind to the evaluation arm; seek a second reader for disputed cases or a sample when available.

## Measures

- **Risk and usefulness:** incorrect permission to answer, unsupported or wrong-version answers, supported-answer precision, answer coverage, and correct answers divided by all answerable cases.
- **Abstention and recovery:** unnecessary abstention, unresolved cases, and successful recovery.
- **Generated answers:** support for material claims and citations, including validation failures and withheld outputs.
- **Resources:** end-to-end p50/p95 latency, retries, tokens, and total cost across judges, generation, retrieval, and recovery.

Plot risk against coverage across thresholds. An always-abstaining system must score poorly on usefulness. Select thresholds on calibration data, then report the frozen operating point on the test set. Use paired comparisons and uncertainty intervals grouped by topic family where feasible.

## Reproducibility and interpretation

Record source hashes, case/split versions, prompts and schemas, requested/resolved model IDs, timestamps, provider responses for the public corpus, and cost assumptions. Clearly distinguish offline mocks, recorded live runs, and fresh API runs.

Publish failures as well as successes, separating retrieval misses, gate mistakes, and generation errors. Controlled bad retrieval and synthetic conflicts must be labeled. One documentation corpus cannot establish general RAG reliability. If metadata rules or the inexpensive LLM offer a better tradeoff, publish that result and retain an interchangeable judge interface.
