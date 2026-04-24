# Workflows

## Purpose

This document explains the main business flows in a step-by-step way that is readable without source code context.

## Order Processing Workflow

1. A user creates an order in `Draft`.
2. The system validates required fields and tenant ownership.
3. The user submits the order.
4. The application schedules asynchronous validation and downstream notifications.
5. Background processing enriches or verifies the order against external dependencies.
6. If validation succeeds, the order moves to `Validated`.
7. A fulfillment step completes the order.
8. If validation fails, the order is marked for manual review.

## Scheduled Reconciliation Workflow

1. A recurring Hangfire job starts for a specific tenant.
2. The worker loads reconciliation candidates for that tenant.
3. The job compares local state with external source-of-truth data.
4. Mismatches are classified as auto-fixable or manual-review cases.
5. Safe fixes are applied.
6. Remaining issues are emitted to an operations queue or review dashboard.
7. A summary is logged with counts and outcome status.

## Escalation Rules

- User-facing workflows should fail fast with actionable validation messages.
- Background reconciliation should prefer flagging ambiguous cases over guessing.
- Cross-tenant or high-impact actions require explicit administrative paths.

## Important Constraints

- Workflows describe intended business flow, not internal method calls.
- The exact state machine should be enforced in code and tests.
- Background jobs are part of workflows when they carry business meaning.
- Operational run steps belong in the runbook, not here.

## Related Documents

- [Business Rules](business-rules.md)
- [Background Jobs](../architecture/background-jobs.md)
- [Local Development Runbook](../runbook/local-development.md)
