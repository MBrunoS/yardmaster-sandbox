# Troubleshooting the sandbox queue

Quick checks when a queued pull request doesn't behave as expected.

## The queue never picks up my PR

- Confirm the PR targets `master` and is not a draft — Yardmaster requires
  `require_ready_for_review` per `.yardmaster.yml`.
- Confirm the PR carries an allowed label if `allow_labels` is configured.

## Validation never completes

- The sandbox validation workflow only asserts `contract_version == "1"`; it
  does not check out or build code. A hang usually means the workflow file
  is missing from `master`, since `workflow_dispatch` always resolves the
  workflow from the default branch.

## The merge was rejected

- Yardmaster re-verifies the exact candidate SHA immediately before asking
  GitHub to merge. If the target branch or PR head moved in the meantime,
  the attempt is marked stale rather than merged.
