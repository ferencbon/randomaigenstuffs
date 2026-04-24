# Greenfield Documentation Sample Repo

This repository demonstrates a lightweight documentation strategy for a greenfield `.NET` system with multi-tenancy and `Hangfire` background processing.

## What This Repo Contains

- a filled sample documentation set under [](index.md)
- a repo-only reusable template under [docs-template/](docs-template/README.md)
- MkDocs configuration for publishing the `` content with GitHub Pages

## Start With The Documentation

The documentation home lives at [index.md](index.md).

Use that page as the real starting point for:

- architecture guidance
- domain rules and workflows
- ADRs
- local development runbooks

## Repository Roles

- `` is the filled reference example that MkDocs publishes.
- `docs-template/` is the copyable template for a new project and is not part of the public docs site.
- `README.md` is a short landing page for GitHub visitors, not the full documentation home.

## Publishing

The published site is built from the `` directory through `mkdocs.yml` and the GitHub Pages workflow in `.github/workflows/docs.yml`.
