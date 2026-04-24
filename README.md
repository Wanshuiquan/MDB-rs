# MDB-rs

Rust rewrite of the MillenniumDB QUAD model for learning and experimentation.

## Goals

1. Rebuild the QUAD model core in Rust with clear module boundaries.
2. Preserve query-facing behavior where practical, while starting with a Rust-native internal format.
3. Learn Rust development systematically through documentation-first milestones and tests-first implementation.

## Non-Goals (Initial Phase)

1. Full feature parity with the whole MillenniumDB server.
2. Binary-compatible on-disk format in milestone 1.
3. Performance tuning before semantic correctness is stable.

## Scope of This Rewrite

Included in phase 1:

1. ObjectId and value model (encoding classes and comparison contract).
2. Quad index permutations for core edge matching patterns.
3. Import pipeline for initial dataset ingestion.
4. Minimal query path for deterministic read scenarios.
5. Documentation and test scaffolding before production code.

Out of scope in phase 1:

1. Full transaction engine.
2. Advanced optimizer internals.
3. Complete CLI/server parity.

## Step-by-Step Plan

### Phase 0: Baseline

1. Create repository documentation skeleton and design contracts.
2. Define milestone acceptance criteria.
3. Add test catalog before implementation.

### Phase 1: Behavior Contracts

1. Lock down ObjectId invariants and value ordering contract.
2. Specify quad index permutation semantics and consistency rules.
3. Define parser error categories and expected diagnostics.

### Phase 2: Crate and Module Design

1. Define workspace structure and dependency direction.
2. Assign responsibility per module with explicit public API boundaries.
3. Create traceability matrix from MillenniumDB components to MDB-rs modules.

### Phase 3: First Implementable Slice

1. Implement ObjectId/value types and round-trip checks.
2. Implement in-memory quad index permutations.
3. Wire parser smoke path and minimal read query path.
4. Run deterministic tests on small fixtures.

### Phase 4: Stabilization

1. Expand behavior tests and negative tests.
2. Validate edge-case ordering and parser corner cases.
3. Prepare decision point for compatibility bridge vs native-only storage.

## Proposed Project and Document Structure

Project structure for the next steps:

1. docs/architecture/overview.md
2. docs/architecture/object-id-and-value-model.md
3. docs/architecture/quad-index-permutations.md
4. docs/architecture/import-pipeline.md
5. docs/roadmap/milestones.md
6. docs/testing/initial-test-cases.md
7. docs/dev/setup-and-workflow.md
8. docs/dev/contributing.md
9. docs/migration/mdb-traceability-matrix.md

Code structure to create when implementation begins:

1. crates/mdb-core (ObjectId, value model, comparison semantics)
2. crates/mdb-index (quad indexes and permutation rules)
3. crates/mdb-parser (input parsing and diagnostics)
4. crates/mdb-query (minimal read query evaluation)
5. crates/mdb-fixtures (shared small datasets for tests)
6. tests/integration (end-to-end semantic checks)

## Initial Test Cases (No Production Code Yet)

1. ObjectId round-trip tests
- Build ObjectId from supported categories and decode back.
- Assert identity and category stability.

2. Value comparison ordering tests
- Compare int/float/string/date-like placeholders under documented rules.
- Assert deterministic total order for mixed types.

3. Quad permutation consistency tests
- Insert same quads across all permutation views.
- Assert all views return consistent edge identity.

4. Parser smoke tests
- Accept minimal valid input files.
- Reject malformed tokens with expected diagnostic class.

5. Minimal query behavior tests
- Run deterministic point lookup and small pattern match.
- Assert exact result set and ordering contract.

See detailed cases in docs/testing/initial-test-cases.md.

## How to Work Through This as a Rust Learning Project

1. Start each milestone by implementing one test group only.
2. Keep public APIs tiny and stable before adding features.
3. Document design decisions in docs/architecture as they change.
4. Prefer correctness and readability before optimization.

## Immediate Next 3 Tasks

1. Create the crate workspace skeleton without business logic.
2. Implement only ObjectId data types and round-trip tests.
3. Implement first in-memory index view and consistency tests.
