# Glossary

## Purpose

This document standardizes the main domain and platform terms used across architecture notes, ADRs, tests, and code reviews.

## Terms

- `Tenant`: A logical customer boundary with isolated business data and configuration.
- `Tenant Context`: The runtime object that identifies the active tenant and related metadata.
- `Order`: A sample business aggregate that moves through a controlled lifecycle.
- `Reconciliation`: A scheduled process that compares internal records with external systems.
- `Administrative Flow`: A privileged path used for cross-tenant support or maintenance actions.
- `Background Job`: Work executed outside the request path through `Hangfire`.
- `Recurring Job`: A scheduled job that runs on a fixed cadence.
- `Lock Scope`: The business or tenant boundary used to prevent unsafe concurrent job execution.
- `Manual Review`: A state where human action is required before workflow continuation.
- `Idempotent Operation`: An operation that can be retried without changing the end result unexpectedly.

## Naming Guidance

- Use `tenant` consistently instead of mixing `account`, `workspace`, or `customer` unless those are explicitly different concepts.
- Use lifecycle state names consistently across docs, tests, and UI text.
- Prefer `background job` for execution model and `workflow` for business process.

## Important Constraints

- If a term becomes overloaded, split it into separate definitions.
- Glossary terms should reflect real product language, not temporary implementation jargon.
- Update this file when a new cross-cutting concept appears in multiple documents.

## Related Documents

- [Business Rules](business-rules.md)
- [Tenancy Model](../architecture/tenancy.md)
- [ADR 001: Hangfire Locking](../adr/001-hangfire-locking.md)
