# cloudflare-subpath-deploy-playground

Integration tests for [`dytsou/cloudflare-subpath-deploy`](../cloudflare-subpath-deploy).

This repo **may** contain `.github/workflows/` (unlike the Marketplace Action repo).

## Fixtures

- `fixtures/sample-contract.json` — example deploy contract
- `fixtures/sample-page/dist/` — minimal static build output
- `fixtures/route-manifest.json` — seed manifest for validation

## Local

```bash
cd ../cloudflare-subpath-deploy
node --check lib/*.mjs
node lib/verify-deploy-contract.mjs --self-check
node lib/verify-route-manifest.mjs --self-check
node lib/upsert-route-manifest.mjs --self-check
node lib/deploy-pages.mjs --self-check
node lib/deploy-worker.mjs --self-check
node lib/smoke-routes.mjs --self-check
```

## CI

`test-action.yml` checks out the Action repo and runs self-checks. Full deploy integration requires Cloudflare secrets (future).
