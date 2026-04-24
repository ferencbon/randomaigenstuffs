# Tenancy Model

## Purpose

This document explains how tenant context is identified, propagated, and enforced across the system.

## Current Design

The sample uses a logical multi-tenant model:

- every request belongs to one tenant
- application behavior is tenant-aware by default
- data access is scoped by tenant identifiers
- background jobs run with explicit tenant context rather than relying on ambient request state

Tenant resolution follows this sequence:

1. Resolve tenant identifier from the authenticated request context.
2. Validate that the caller is allowed to act for that tenant.
3. Load tenant configuration and feature flags.
4. Propagate tenant context into application services, repositories, and jobs.

## Isolation Rules

- Tenant data is filtered by tenant identifier in every application query path.
- Shared infrastructure may be global, but business data is tenant-scoped.
- Cross-tenant operations are treated as administrative workflows and must be explicit.
- Background processing never assumes a default tenant.

## Operational Considerations

- Logs should include tenant identifiers where available.
- Metrics should allow per-tenant visibility for throughput and failures.
- Seed data for local development should include multiple tenants to expose isolation bugs early.
- Support tooling should make tenant context visible to operators.

## Important Constraints

- Tenant resolution must happen once, near the boundary of the system.
- Services should depend on a tenant context abstraction, not on HTTP types.
- Tenant scope is a business boundary as well as a technical boundary.
- Exact rationale for this model is captured in the ADR, not repeated here.

## Related Documents

- [Architecture Overview](overview.md)
- [Business Rules](../domain/business-rules.md)
- [Glossary](../domain/glossary.md)
- [ADR 002: Multi-Tenant Model](../adr/002-multi-tenant-model.md)
