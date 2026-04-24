# Architecture Overview

## Objective

Define a clean Rust architecture for the MillenniumDB QUAD model rewrite.

## Design Principles

1. Correctness first, then performance.
2. Small and testable modules.
3. Explicit behavior contracts for ordering and identity semantics.
4. Deterministic tests over small fixtures before scaling.

## Subsystem Boundaries

1. Core model
- ObjectId category model
- value types
- comparison semantics

2. Index layer
- quad storage views
- permutation maintenance and consistency

3. Import layer
- parser/tokenizer
- diagnostics and error categories

4. Query layer
- minimal read query path
- deterministic result ordering

## Dependency Direction

1. Query depends on Index and Core.
2. Parser depends on Core for typed values.
3. Index depends on Core for key semantics.
4. Core has no dependency on higher layers.

## Milestone Contract

Each milestone must include:

1. one architecture note update,
2. one focused test group,
3. one small implementation slice.