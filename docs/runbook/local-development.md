# Local Development Runbook

## Purpose

This document explains how an engineer would run and troubleshoot the sample system locally.

## Current Setup Expectations

The sample assumes a local development environment with:

- `.NET SDK` installed
- local access to the application source
- a local or containerized backing store
- `Hangfire` storage configured for development
- sample seed data for at least two tenants

Because this repository is documentation-only, the commands below are representative rather than executable in this repo.

## Startup Flow

1. Copy local environment variables from the project template or `.env.example`.
2. Start required infrastructure such as database, cache, and local job storage.
3. Apply seed data for multiple tenants.
4. Start the application API.
5. Start the Hangfire dashboard or worker host if it is separated from the API.
6. Verify that requests resolve the correct tenant context.

## Required Configuration

Typical local settings:

- `ConnectionStrings__PrimaryDatabase`
- `Hangfire__StorageConnectionString`
- `Auth__Authority`
- `Auth__Audience`
- `Tenancy__DefaultTenantMode`
- `ExternalServices__SampleApiBaseUrl`

Use placeholders only. Never commit real credentials or tenant secrets.

## Local Data Guidance

- Keep seed data small and readable.
- Always include at least two tenants.
- Include one workflow that succeeds and one that ends in manual review.
- Include one recurring job scenario that is safe to rerun.

## Troubleshooting

- If all requests appear under one tenant, inspect tenant resolution and request headers or claims.
- If jobs fail locally, verify tenant context is present in the queued payload.
- If recurring jobs overlap, inspect lock configuration and local Hangfire storage.
- If tests pass but workflows look wrong, review domain documents and seed assumptions for drift.

## Important Constraints

- Operational steps belong here, not in architecture docs.
- Exact local commands should live in a real project repo once the application exists.
- This runbook should stay short and biased toward the problems new engineers actually hit.

## Related Documents

- [Architecture Overview](../architecture/overview.md)
- [Background Jobs](../architecture/background-jobs.md)
- [Business Rules](../domain/business-rules.md)
