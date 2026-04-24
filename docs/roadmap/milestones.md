# Milestones

## M0: Documentation and Test Blueprint

Deliverables:

1. Architecture docs complete for core subsystems.
2. Initial cross-layer test-case catalog complete.
3. Full-system project structure and dependency direction defined.

Exit criteria:

1. README includes step-by-step implementation plan.
2. Each planned module has at least one test group.

## M1: Core and Storage Foundation

Deliverables:

1. ObjectId and value types implemented.
2. Catalog metadata and storage contracts implemented.
3. Round-trip and ordering tests passing.

Exit criteria:

1. Deterministic behavior on fixture set.
2. No panics on invalid input in covered tests.
3. Storage metadata persists and reloads under tests.

## M2: Quad Index Slice

Deliverables:

1. Initial permutation views implemented.
2. Consistency tests passing for insert/delete/lookup.
3. Integrity checks pass after restart/reload paths.

Exit criteria:

1. Cross-view parity verified on non-trivial fixtures.

## M3: Import, Export, and Query Slice

Deliverables:

1. Parser and validation pipeline implemented for initial qm/csv coverage.
2. Export path implemented for deterministic dumps.
3. Query read path implemented for core quad patterns.

Exit criteria:

1. Import/export/query smoke tests pass in CI.

## M4: Update and Transaction Semantics

Deliverables:

1. Insert/delete/update action pipeline implemented.
2. Atomicity and consistency strategy documented and tested.

Exit criteria:

1. Update regression tests pass with deterministic fixtures.
2. Index and catalog state remains consistent after failed updates.

## M5: CLI and Server Runtime

Deliverables:

1. CLI commands for import/query/admin workflows implemented.
2. Server mode request lifecycle implemented.

Exit criteria:

1. End-to-end cli and server smoke tests pass.

## M6: Compatibility and Hardening Gate

Options:

1. Keep Rust-native format only.
2. Add bridge import/export for MillenniumDB artifacts.
3. Start binary compatibility work.

Decision input:

1. Learning goals
2. correctness status
3. maintenance cost