# ADR 001: Use Filter-Based Locking For Hangfire Jobs

## Purpose

Record why the system applies concurrency control for selected `Hangfire` jobs through filters instead of embedding locking code inside each job handler.

## Context

Some jobs must not run concurrently for the same tenant or business scope. Examples include reconciliation, settlement-style processing, or cache rebuilds that mutate shared state.

If each job implements its own locking behavior, the system tends to drift:

- lock behavior becomes inconsistent
- business code gets mixed with operational concerns
- observability and retry handling vary across handlers

## Decision

Use filter-based locking for jobs that require scoped mutual exclusion.

The lock is applied through Hangfire infrastructure so that:

- the locking policy is declared centrally
- business handlers stay focused on domain work
- logging and failure behavior remain consistent
- new jobs can opt into locking without copying infrastructure code

## Rationale

This approach keeps concurrency policy near job execution infrastructure, which is where retry and scheduling behavior already lives.

It also makes lock behavior easier to review and test because the pattern is shared across jobs instead of being reimplemented case by case.

## Consequences

Positive:

- less duplicated locking code
- clearer separation between business logic and operational control
- easier to apply consistent telemetry

Trade-offs:

- filter behavior must be well understood by maintainers
- debugging may require knowledge of Hangfire pipeline behavior
- lock-key design becomes an important shared concern

## Alternatives Considered

- Put locking directly in each job handler
  - rejected because it duplicates infrastructure concerns and invites drift
- Use only database-level protection
  - rejected because it protects data integrity but does not provide a clear job-level execution model
- Avoid locking and rely on idempotency alone
  - rejected because some workflows still require controlled sequencing

## Related Documents

- [Background Jobs](../architecture/background-jobs.md)
- [Glossary](../domain/glossary.md)
