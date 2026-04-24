# ObjectId and Value Model

## Purpose

Describe the Rust-side contract for ObjectId and values before coding.

## Behavior Contract

1. ObjectId must preserve stable category identity.
2. Encoding and decoding must be deterministic.
3. Value comparison must be total and deterministic.
4. Error cases must return typed diagnostics, not panic.

## Initial Categories

1. Fixed node inside
2. Edge
3. Named node
4. String
5. Scalar number placeholder
6. Reserved categories for future expansion

## Initial Implementation Notes

1. Keep representation opaque behind constructor functions.
2. Avoid exposing raw internal bit layout in first iteration.
3. Add dedicated round-trip tests per category.

## Test Requirements

1. Round-trip idempotence across all supported categories.
2. Invalid input detection and stable error tags.
3. Mixed-value ordering remains deterministic across runs.