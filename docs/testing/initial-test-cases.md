# Initial Test Cases

This document defines the first executable tests to build before broad implementation.

Scope note:

1. Tests target full-system behavior under QUAD-only model support.

## Dataset Fixtures

Use tiny deterministic fixtures:

1. fixture_a: 3 nodes, 2 edge types, 5 edges
2. fixture_b: duplicate labels and shared endpoints
3. fixture_invalid: malformed records for parser diagnostics

## Group A: ObjectId Round-Trip

Cases:

1. Construct each supported ObjectId category and decode it back.
2. Encode-decode-encode cycle remains stable.
3. Invalid constructor input returns expected error kind.

Assertions:

1. Category and payload match expected values.
2. No panics.

## Group B: Value Comparison Contract

Cases:

1. Same-type comparisons for all supported scalar placeholders.
2. Mixed-type comparisons under documented total-order rule.
3. Boundary-like values and empty string behavior.

Assertions:

1. Ordering is deterministic and transitive.
2. Sorting same input twice yields same sequence.

## Group C: Quad Permutation Consistency

Cases:

1. Insert fixture_a and validate all permutations can find expected edges.
2. Delete subset and verify no stale references remain.
3. Reinsert and verify idempotence policy behavior (document chosen policy).

Assertions:

1. Result sets from different access paths refer to same edge identity.
2. Iteration order is deterministic for test execution.

## Group D: Parser Smoke and Diagnostics

Cases:

1. Valid minimal input imports successfully.
2. Missing field returns MissingField.
3. Invalid token returns InvalidToken.
4. Duplicate edge id returns DuplicateEdgeId.

Assertions:

1. Error category and location are stable.
2. Negative cases never partially mutate index state unless documented.

## Group E: Minimal Query Behavior

Cases:

1. Exact edge lookup by from, to, type.
2. Lookup by type-only path using permutation index.
3. No-match scenario returns empty deterministic result.

Assertions:

1. Output edge identities are exact.
2. Ordering contract is preserved.

## Group F: Update Semantics

Cases:

1. Insert edge then query by multiple index paths.
2. Delete edge then assert complete removal from all views.
3. Update property and verify visibility in query path.

Assertions:

1. No partial state persists after failed updates.
2. Catalog counters remain consistent.

## Group G: CLI and Server Smoke

Cases:

1. CLI import then CLI query returns deterministic output.
2. Server startup and one request lifecycle completes successfully.

Assertions:

1. Exit codes and response categories are stable.
2. Minimal operational workflow is reproducible.

## Group H: Recovery and Persistence

Cases:

1. Persist fixture, restart runtime, query same data.
2. Run integrity checker after restart.

Assertions:

1. Results before and after restart are equivalent.
2. No metadata/index mismatch is detected.

## Suggested Command Sequence Once Test Harness Exists

1. cargo fmt --all -- --check
2. cargo clippy --workspace --all-targets -- -D warnings
3. cargo test --workspace
4. cargo test --test integration_smoke

## Done Definition for Initial Steps

1. Groups A, B, C pass.
2. At least one case from D, E, and F passes.
3. At least one smoke case from G or H passes.
3. Failures include actionable diagnostic messages.