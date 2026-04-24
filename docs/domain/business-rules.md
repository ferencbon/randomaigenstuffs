# Business Rules

## Purpose

This document captures the non-trivial business rules that engineers and product stakeholders need to interpret the system consistently.

## Current Rules

Sample rules for this repository:

- Every business record belongs to exactly one tenant.
- A tenant can only access and modify its own active records.
- Orders move forward through their lifecycle and cannot skip mandatory states.
- A completed order becomes read-only except for approved correction flows.
- Scheduled reconciliation may flag an order for review, but it does not auto-complete manual approval steps.

## Validation Boundaries

- Input shape validation happens at the system boundary.
- Domain validation happens in application and domain logic.
- Referential checks against external systems happen before irreversible transitions.
- Background jobs re-validate business preconditions because state may change between enqueue and execution.

## Lifecycle Rules

Example order lifecycle:

1. `Draft` can be edited freely.
2. `Submitted` is awaiting automated validation.
3. `Validated` is ready for fulfillment.
4. `Completed` is closed for normal edits.
5. `Cancelled` is terminal and requires an explicit reason.

## Tenant-Scoped Rules

- Uniqueness is evaluated within a tenant unless a rule is explicitly global.
- Feature enablement may differ by tenant.
- SLA and processing windows may vary by tenant contract.
- A support user may act across tenants only through audited administrative flows.

## Important Constraints

- This document describes business intent, not implementation classes or methods.
- Exact behavior should be backed by automated tests.
- Technical enforcement details belong in architecture docs.
- Decision history belongs in ADRs.

## Related Documents

- [Workflows](workflows.md)
- [Glossary](glossary.md)
- [Tenancy Model](../architecture/tenancy.md)
