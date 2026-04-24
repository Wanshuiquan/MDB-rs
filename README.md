# MDB-rs

Rust rewrite of the full MillenniumDB system with only the QUAD model variant.

## Goals

1. Rebuild the full MillenniumDB architecture in Rust while supporting only the QUAD model.
2. Preserve core query and update behavior from MillenniumDB for QUAD workloads.
3. Deliver a maintainable, modular Rust codebase with clear boundaries and testable contracts.

## Non-Goals (Initial Phase)

1. Multi-model support (RDF, Property Graph, GQL variants beyond QUAD).
2. Perfect binary compatibility in early milestones.
3. Early performance tuning before semantic correctness and reliability are stable.

## Scope of This Rewrite

Included in full-system scope:

1. Core data model and ObjectId/value semantics for QUAD.
2. Storage and index subsystem for quad permutations.
3. Import and export pipelines.
4. Query parser, planner, and executor for QUAD-relevant features.
5. Update execution path with correctness guarantees.
6. CLI and server runtime.
7. System metadata, catalog lifecycle, and operational tooling.
8. Evaluation and regression test infrastructure.

Out of scope for this repository:

1. Non-QUAD model implementations.
2. Experimental features not required for QUAD parity.

## Step-by-Step Plan

### Phase 0: Baseline

1. Create repository documentation skeleton and design contracts.
2. Define full-system milestone acceptance criteria.
3. Add cross-layer test catalog before implementation.

### Phase 1: Behavior Contracts

1. Lock down ObjectId invariants and value ordering contract.
2. Specify quad index permutation semantics and consistency rules.
3. Define import, query, update, and runtime error contracts.

### Phase 2: System Architecture and Crate Design

1. Define workspace structure for all major MillenniumDB subsystems.
2. Assign crate ownership for storage, query, update, import/export, cli, and server.
3. Create traceability matrix from MillenniumDB components to MDB-rs crates.

### Phase 3: Core Engine Foundation

1. Implement ObjectId/value types and round-trip checks.
2. Implement initial quad index engine and catalog metadata.
3. Wire import path and deterministic storage tests.
4. Validate recovery and integrity checks in local fixtures.

### Phase 4: Query and Update Stack

1. Implement parser, logical planning interface, and execution pipeline.
2. Implement update pipeline with atomicity strategy.
3. Add conformance tests for read and write semantics.

### Phase 5: Runtime and Tooling

1. Implement CLI workflows for import, query, and administration.
2. Implement server mode and request execution lifecycle.
3. Add operational checks, metrics hooks, and debug tooling.

### Phase 6: Compatibility and Hardening

1. Expand import/export compatibility with MillenniumDB artifacts.
2. Run regression suites and larger benchmarks.
3. Close parity gaps and publish stabilization checklist.

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
2. crates/mdb-storage (catalog, persistence, index management)
3. crates/mdb-index (quad index permutations and lookup paths)
4. crates/mdb-import (qm/csv import and validation)
5. crates/mdb-export (dump and serialization paths)
6. crates/mdb-query (parser, planner interfaces, execution)
7. crates/mdb-update (insert/delete/update actions)
8. crates/mdb-cli (command-line entry points)
9. crates/mdb-server (server runtime)
10. crates/mdb-fixtures (shared deterministic datasets)
11. tests/integration (cross-subsystem semantic checks)
12. tests/e2e (cli/server black-box checks)

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

5. Query behavior tests
- Run deterministic point lookup, pattern match, and filter scenarios.
- Assert exact result set and ordering contract.

6. Update behavior tests
- Insert, delete, and modify edges/properties under deterministic fixtures.
- Assert index consistency and visibility after updates.

7. CLI and server smoke tests
- Validate import/query flows through cli commands.
- Validate one minimal server request lifecycle.

See detailed cases in docs/testing/initial-test-cases.md.

## How to Work Through This as a Rust Learning Project

1. Start each milestone by implementing one test group only.
2. Keep public APIs tiny and stable before adding features.
3. Document design decisions in docs/architecture as they change.
4. Prefer correctness and readability before optimization.

## Immediate Next 3 Tasks

1. Create full crate workspace skeleton for all core subsystems.
2. Implement ObjectId plus storage catalog metadata contracts and tests.
3. Implement initial query/update smoke pipeline over quad indexes.
