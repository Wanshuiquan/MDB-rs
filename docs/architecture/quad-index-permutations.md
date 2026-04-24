# Quad Index Permutations

## Purpose

Define the index consistency contract for quad access patterns.

## Core Quad Shape

Quad logical tuple:

1. from
2. to
3. type
4. edge

## Initial Permutations to Support

1. from_to_type_edge
2. to_type_from_edge
3. type_from_to_edge
4. type_to_from_edge
5. edge_from_to_type

## Consistency Rules

1. One logical insertion must update all enabled views.
2. Deletion must remove the quad from all enabled views.
3. Query through any permutation must refer to the same edge identity.
4. Partial update failure handling must be explicit and testable.

## Early Implementation Strategy

1. Start with in-memory map-based prototype.
2. Validate semantics before storage optimization.
3. Add test fixtures with repeated labels and shared endpoints.

## Test Requirements

1. Insert same dataset and assert lookup parity across views.
2. Delete selected edges and assert no stale entries.
3. Verify deterministic iteration order for test stability.