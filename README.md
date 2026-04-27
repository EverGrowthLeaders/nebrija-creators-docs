# Nebrija Creators Docs

Standalone Fern repository for Nebrija Creators API documentation.

Last deployment trigger: 2026-04-27.

## Structure

```text
fern/
  fern.config.json
  docs.yml
  generators.yml
  openapi.yml
  docs/pages/*.mdx
.github/workflows/publish-docs.yml
```

## Local validation

```bash
npm install -g fern-api
fern check --warnings
fern docs dev
```

## Preview

```bash
FERN_TOKEN=... fern generate --docs --preview
```

## Production publish

The workflow `.github/workflows/publish-docs.yml` validates pull requests and publishes on pushes to `main` that modify `fern/**`.

Required secret:

```text
FERN_TOKEN
```

Target instance:

```text
nebrija-creators.docs.buildwithfern.com
```

## Decisions and weak points

- This repo is intentionally docs-only. It does not contain the Nebrija Creators application code.
- The production API host in `openapi.yml` is set to `https://creators.nebrija.ai/api/v1`. If the final public domain differs, update the server URL before merging.
- No custom domain is configured yet. Add `custom-domain: docs.<domain>` in `fern/docs.yml` once DNS is decided.
- Fern CLI is pinned to `4.43.0` to match the existing Nebrija AI docs setup. Run `fern upgrade` later if you want to move this docs repo to a newer CLI.
