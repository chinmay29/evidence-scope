# Contributing

EvidenceScope is at the design and initial-scaffold stage. Start with the
[architecture](docs/architecture.md), [evaluation plan](docs/evaluation.md) and
[roadmap](docs/roadmap.md).

Useful early contributions include reviewing the evidence contract, identifying
version-sensitive documentation questions, and improving the evaluation design.
Open an issue before starting a substantial implementation so it fits the current
milestone.

For proposed evaluation cases, include the question, requested version/API scope,
public source URL, supporting passages and a human explanation of the expected
judgment. Clearly label synthetic or modified evidence. Keep closely related
cases together to avoid leaking information across evaluation splits.

For code contributions, separate deterministic policy from model judgments,
include tests for material behavior and failure paths, and preserve the one-retry
retrieval budget. Offline checks should not require paid API access. Development
commands will be documented when the implementation is available.

Never commit credentials, private customer data or unreviewed provider traces.
Do not report recorded fixtures or mocks as live benchmark measurements. Attribute
external material and preserve its license requirements.
