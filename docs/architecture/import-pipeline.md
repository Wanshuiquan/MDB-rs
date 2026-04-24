# Import Pipeline

## Purpose

Define initial import behavior and parser quality gates.

## Phase 1 Scope

1. Minimal line-oriented parser path.
2. Support small deterministic fixture datasets.
3. Emit structured diagnostics for malformed records.

## Pipeline Stages

1. Input read
2. Token parse
3. Typed conversion
4. Validation
5. Insert into index layer

## Error Categories

1. Invalid token
2. Missing field
3. Invalid value category
4. Duplicate edge identifier
5. Internal consistency error

## Test Requirements

1. Positive smoke file imports correctly.
2. Malformed file returns expected error category.
3. Mixed valid and invalid records produce deterministic result or fail-fast behavior (decision documented).