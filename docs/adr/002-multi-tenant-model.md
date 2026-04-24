# ADR 002: Use A Logical Multi-Tenant Application Model

## Purpose

Record why the sample system uses a logical multi-tenant model with explicit tenant context propagation.

## Context

The system serves multiple tenants with the same application stack. Each tenant needs isolated business data, tenant-specific configuration, and auditable request processing.

The design must balance:

- operational simplicity
- strong tenant boundaries
- developer ergonomics
- support for tenant-aware background jobs

## Decision

Use a logical multi-tenant model where:

- tenant identity is resolved at the boundary of the system
- application services and repositories operate with explicit tenant context
- business data is scoped by tenant identifier
- background jobs carry tenant context explicitly when enqueued

## Rationale

This model provides a clear default for engineers: all business operations are tenant-scoped unless explicitly documented otherwise.

It supports shared infrastructure while keeping business isolation visible in both runtime behavior and code structure.

It also fits background processing well because job payloads can carry the same tenant boundary used by synchronous requests.

## Consequences

Positive:

- clear default isolation model
- simpler operational footprint than fully separate deployments per tenant
- consistent behavior between request-driven and job-driven execution

Trade-offs:

- strict discipline is required in query and repository design
- tenant leaks can become application bugs if boundaries are bypassed
- support and reporting flows need explicit cross-tenant controls

## Alternatives Considered

- Single-tenant deployment per customer
  - rejected because it increases operational overhead for the sample’s target complexity
- Weak tenant awareness at the UI layer only
  - rejected because isolation must be enforced in backend processing
- Fully shared data without tenant scoping
  - rejected because it does not meet isolation expectations

## Related Documents

- [Tenancy Model](../architecture/tenancy.md)
- [Business Rules](../domain/business-rules.md)
