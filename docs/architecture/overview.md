# Architecture Overview

## Objective

Define a clean Rust architecture for a full MillenniumDB rewrite constrained to the QUAD model.

## Design Principles

1. Correctness first, then performance.
2. Modular subsystems with explicit contracts.
3. Explicit behavior contracts for ordering and identity semantics.
4. Deterministic tests from unit to end-to-end layers before scaling.
5. One supported model variant (QUAD) across all subsystems.

## Subsystem Boundaries

1. Core model
- ObjectId category model
- value types
- comparison semantics

2. Storage and catalog layer
- persistent metadata and catalog lifecycle
- storage abstractions and recovery hooks

3. Index layer
- quad storage views
- permutation maintenance and consistency

4. Import/export layer
- parser/tokenizer
- diagnostics and error categories
- deterministic dump serialization

5. Query and update layer
- parser and execution pipeline
- read and write semantics
- deterministic result ordering

6. Runtime layer
- cli command workflows
- server request lifecycle

7. Testing and evaluation layer
- unit, integration, and end-to-end suites
- regression fixtures and benchmark harnesses

## Dependency Direction

1. Core has no dependency on higher layers.
2. Storage and Index depend on Core.
3. Import/export depends on Core plus Storage/Index interfaces.
4. Query/update depends on Core, Index, and Storage interfaces.
5. Runtime depends on query/update and import/export application services.
6. Tests may depend on all layers through public APIs only.

## Milestone Contract

Each milestone must include:

1. one architecture note update,
2. one focused test group,
3. one implementation slice in at least one subsystem,
4. one explicit parity checkpoint versus MillenniumDB behavior.