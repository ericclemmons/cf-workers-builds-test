# cf Workers Builds test

Official `cf init` Hello World starter, pinned to `cf@1.0.0-beta.31`.
Uses `cloudflare.config.ts` and a local `cf` dependency, with no Wrangler config.
Node.js is pinned to 24.22.1 for Workers Builds.

## Connect to Workers Builds

Import this repository through Workers & Pages. Use the repository root and `main` as the production branch.
To test the Worker-name override, name the connected Worker `cf-workers-builds-dashboard-test`; the config deliberately keeps `cf-workers-builds-test`.

Expected autofilled commands:

| Field | Value |
| --- | --- |
| Build command | `npx cf build` |
| Deploy command | `npx cf deploy --prebuilt` |
| Preview build command, when shown separately | Empty |
| Preview deploy command | `npx cf previews deploy` |

After the first build, the connected Worker's URL should return `Hello World!`.
The build should report the name override, and deployment should target the connected Worker.

To check previews, create a branch and change the response in `src/index.ts`.
Its preview URL should show the branch greeting while production keeps `Hello World!`.
Also check that a manually edited dashboard command survives autofill.

## Local checks

```sh
npm ci
npm run typecheck
npm run build
```

This repository has not been deployed by its setup script. Production and preview deployment checks must be performed through Workers Builds.

## References

- [Official cf starter](https://github.com/cloudflare/cf/tree/cf%401.0.0-beta.31/packages/cli/src/commands/init)
- [cf beta.31 release](https://github.com/cloudflare/cf/releases/tag/cf%401.0.0-beta.31)
