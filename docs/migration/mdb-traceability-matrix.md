# MillenniumDB to MDB-rs Traceability Matrix

## Purpose

Map source responsibilities from MillenniumDB QUAD model to planned MDB-rs modules.

## Matrix

1. MillenniumDB: src/graph_models/quad_model/quad_model.h, quad_model.cc
- MDB-rs target: crates/mdb-index and docs/architecture/quad-index-permutations.md
- Responsibility: quad index topology and consistency semantics

2. MillenniumDB: src/graph_models/quad_model/quad_catalog.h, quad_catalog.cc
- MDB-rs target: future storage metadata module and docs/roadmap/milestones.md
- Responsibility: metadata tracking and versioning strategy

3. MillenniumDB: src/graph_models/quad_model/quad_object_id.h, quad_object_id.cc
- MDB-rs target: crates/mdb-core and docs/architecture/object-id-and-value-model.md
- Responsibility: ObjectId conversion and identity categories

4. MillenniumDB: src/graph_models/quad_model/comparisons.cc
- MDB-rs target: crates/mdb-core and docs/testing/initial-test-cases.md
- Responsibility: ordering and comparison contract

5. MillenniumDB: src/import/quad_model/import.h
- MDB-rs target: crates/mdb-parser and docs/architecture/import-pipeline.md
- Responsibility: parser stages and diagnostics

6. MillenniumDB: query executor and update modules
- MDB-rs target: crates/mdb-query (minimal read path first)
- Responsibility: query-facing behavior for initial deterministic scenarios

## Notes

1. This rewrite starts with Rust-native internal format.
2. Binary compatibility is deferred to a later decision gate.