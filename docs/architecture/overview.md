# Architecture Overview

## Purpose

This document explains how the sample system is structured and where to look for the main technical responsibilities.

## Current Design

The sample system is a multi-tenant `.NET` application with synchronous request handling and asynchronous background processing.

Main components:

- `API layer` handles authenticated HTTP requests and tenant resolution.
- `Application layer` coordinates use cases and enforces business workflows.
- `Domain layer` contains business rules and validations.
- `Infrastructure layer` handles persistence, external integrations, caching, and background job scheduling.
- `Hangfire workers` execute deferred and recurring work outside the request path.

## Request Flow

1. An incoming request is authenticated.
2. Tenant context is resolved from the request.
3. The application executes tenant-scoped business logic.
4. The request either completes synchronously or schedules a background job.
5. Logs and metrics include tenant-aware correlation data.

## Important Constraints

- Tenant context must be established before domain logic runs.
- Business rules live in code and tests, not in controller or worker glue code.
- Background jobs must be safe to retry and safe to run per tenant.
- Architecture documents explain behavior; ADRs explain why key decisions were chosen.

## Related Documents

- [Tenancy Model](tenancy.md)
- [Background Jobs](background-jobs.md)
- [Business Rules](../domain/business-rules.md)
- [ADR 002: Multi-Tenant Model](../adr/002-multi-tenant-model.md)
