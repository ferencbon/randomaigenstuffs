# Documentation Home

This site is the filled example documentation set for a greenfield `.NET` system with multi-tenancy and `Hangfire`.

The goal is to keep documentation useful, small, and maintainable:

- document during delivery, not after it
- capture non-trivial decisions and rules
- avoid duplicating code or tests
- keep the reading path obvious for a new engineer

## Start Here

If you are new to the system, read in this order:

1. [Architecture Overview](architecture/overview.md)
2. [Tenancy Model](architecture/tenancy.md)
3. [Background Jobs](architecture/background-jobs.md)
4. [Business Rules](domain/business-rules.md)
5. [Workflows](domain/workflows.md)
6. [Local Development Runbook](runbook/local-development.md)

Then read the decision log:

- [ADR 001: Hangfire Locking](adr/001-hangfire-locking.md)
- [ADR 002: Multi-Tenant Model](adr/002-multi-tenant-model.md)

## Documentation Model

- `Architecture` explains how the system works.
- `Domain` explains business meaning, rules, and workflow intent.
- `ADR` explains why important technical decisions were made.
- `Code + tests` remain the source of exact behavior.

## Main Sections

### Architecture

Use these pages to understand system shape, boundaries, and runtime behavior.

- [Overview](architecture/overview.md)
- [Tenancy](architecture/tenancy.md)
- [Background Jobs](architecture/background-jobs.md)

### Domain

Use these pages to understand business meaning without diving into code first.

- [Business Rules](domain/business-rules.md)
- [Workflows](domain/workflows.md)
- [Glossary](domain/glossary.md)

### ADR

Use ADRs to understand why the current implementation direction exists.

- [ADR 001: Hangfire Locking](adr/001-hangfire-locking.md)
- [ADR 002: Multi-Tenant Model](adr/002-multi-tenant-model.md)

### Runbook

Use operational notes when you need to run or troubleshoot the system locally.

- [Local Development](runbook/local-development.md)
