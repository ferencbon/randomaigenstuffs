# Background Jobs

## Purpose

This document explains how the sample system uses `Hangfire` for deferred and recurring work.

## Current Design

Background jobs are used for work that should not block user requests:

- outbound integration sync
- scheduled reconciliation
- retryable notification delivery
- maintenance tasks such as cache refresh or stale-record cleanup

Job types:

- `fire-and-forget` for short asynchronous follow-up work
- `scheduled` for delayed execution
- `recurring` for operational and reconciliation tasks

Each job carries explicit tenant context and correlation metadata.

## Locking And Concurrency

The system uses filter-based locking for jobs that must not overlap for the same tenant or business aggregate.

Operational behavior:

- the lock is applied centrally through Hangfire filters
- workers stay focused on business logic
- lock keys are derived from job type and business scope
- jobs that cannot acquire a lock are retried or skipped based on job policy

The reason this is done with filters is documented in the ADR.

## Failure Handling

- Jobs must be idempotent where practical.
- Retry behavior is defined per job category, not assumed globally.
- Permanent failures should produce actionable logs and alerts.
- Poison-job scenarios should move work into manual investigation paths.

## Observability Expectations

- Log job start, completion, retry, and failure events.
- Include job type, tenant identifier, and correlation identifiers.
- Measure queue latency, run duration, retry counts, and failure rates.
- Make recurring job health visible in operations dashboards.

## Important Constraints

- Job handlers must not depend on request-scoped services.
- Tenant context must be rehydrated inside the worker execution path.
- Exact locking rationale belongs in ADRs, not in the architecture layer.
- Tests should prove retry safety and tenant-aware behavior.

## Related Documents

- [Architecture Overview](overview.md)
- [Workflows](../domain/workflows.md)
- [ADR 001: Hangfire Locking](../adr/001-hangfire-locking.md)
