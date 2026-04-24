# Milestones

## M0: Documentation and Test Blueprint

Deliverables:

1. Architecture docs complete for core subsystems.
2. Initial test-case catalog complete.
3. Project structure and dependency direction defined.

Exit criteria:

1. README includes step-by-step implementation plan.
2. Each planned module has at least one test group.

## M1: Core Identity and Value Slice

Deliverables:

1. ObjectId and value types implemented.
2. Round-trip and ordering tests passing.

Exit criteria:

1. Deterministic behavior on fixture set.
2. No panics on invalid parse input in covered tests.

## M2: Quad Index Slice

Deliverables:

1. Initial permutation views implemented.
2. Consistency tests passing for insert/delete/lookup.

Exit criteria:

1. Cross-view parity verified on non-trivial fixtures.

## M3: Import and Minimal Query Slice

Deliverables:

1. Parser smoke pipeline implemented.
2. Minimal read queries over indexed quads implemented.

Exit criteria:

1. Parser and query smoke tests pass in CI.

## M4: Compatibility Decision Gate

Options:

1. Keep Rust-native format only.
2. Add bridge import/export for MillenniumDB artifacts.
3. Start binary compatibility work.

Decision input:

1. Learning goals
2. correctness status
3. maintenance cost