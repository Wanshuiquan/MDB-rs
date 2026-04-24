# Setup and Workflow

## Toolchain

1. Install stable Rust toolchain.
2. Install clippy and rustfmt components.
3. Use a single pinned toolchain version for reproducibility.

## Recommended Daily Workflow

1. Pick one small test group.
2. Write failing tests.
3. Implement minimum logic to pass.
4. Run fmt, clippy, tests.
5. Update docs if behavior changed.

## Quality Gates

1. Formatting check passes.
2. Lint check passes with warnings denied.
3. Unit and integration tests pass.
4. New behavior documented in architecture notes.

## Branch and Commit Practice

1. One milestone task per branch.
2. Keep commits small and explanatory.
3. Include test intent in commit message body.