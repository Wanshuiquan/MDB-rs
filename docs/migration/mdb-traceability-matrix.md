# MillenniumDB to MDB-rs Traceability Matrix

## Purpose

Map source responsibilities from the whole MillenniumDB system to planned MDB-rs modules, with only QUAD model support.

## Matrix

1. MillenniumDB: src/graph_models/quad_model/quad_model.h, quad_model.cc
- MDB-rs target: crates/mdb-index and docs/architecture/quad-index-permutations.md
- Responsibility: quad index topology and consistency semantics

2. MillenniumDB: src/graph_models/quad_model/quad_catalog.h, quad_catalog.cc
- MDB-rs target: crates/mdb-storage and docs/roadmap/milestones.md
- Responsibility: metadata tracking and versioning strategy

3. MillenniumDB: src/graph_models/quad_model/quad_object_id.h, quad_object_id.cc
- MDB-rs target: crates/mdb-core and docs/architecture/object-id-and-value-model.md
- Responsibility: ObjectId conversion and identity categories

4. MillenniumDB: src/graph_models/quad_model/comparisons.cc
- MDB-rs target: crates/mdb-core and docs/testing/initial-test-cases.md
- Responsibility: ordering and comparison contract

5. MillenniumDB: src/import/quad_model/import.h
- MDB-rs target: crates/mdb-import and docs/architecture/import-pipeline.md
- Responsibility: parser stages and diagnostics

6. MillenniumDB: src/import/quad_model/csv and dump/export paths
- MDB-rs target: crates/mdb-import and crates/mdb-export
- Responsibility: csv import behavior and deterministic export compatibility

7. MillenniumDB: src/query/parser, src/query/executor/query_executor/mql
- MDB-rs target: crates/mdb-query
- Responsibility: query parsing, planning boundaries, and execution semantics

8. MillenniumDB: src/query/update/mql
- MDB-rs target: crates/mdb-update
- Responsibility: insert/delete/update semantics and consistency behavior

9. MillenniumDB: src/cli and src/bin/mdb.cc command surface
- MDB-rs target: crates/mdb-cli
- Responsibility: command-line workflows for import, query, and administration

10. MillenniumDB: src/network/server and runtime entrypoints
- MDB-rs target: crates/mdb-server
- Responsibility: server request lifecycle and execution orchestration

11. MillenniumDB: src/storage/index and system services
- MDB-rs target: crates/mdb-storage and crates/mdb-index
- Responsibility: persistence/index backend contracts and integrity checks

12. MillenniumDB: evaluation and tests directories
- MDB-rs target: tests/integration, tests/e2e, crates/mdb-fixtures
- Responsibility: parity regression, benchmark scaffolding, and reproducible fixtures

## Notes

1. This rewrite starts with Rust-native internal format.
2. Binary compatibility is deferred to a later decision gate.
3. QUAD is the only supported model variant in MDB-rs.