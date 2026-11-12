# cf Workers Builds test

Official `cf init` Hello World starter using `cf@latest`.
Fresh installs resolve the latest published cf release; this fixture intentionally has no lockfile.
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

## Create another starter

```sh
npx cf@latest init my-cf-worker --package-manager npm
```

## Local checks

```sh
npm install
npm run typecheck
npx cf@latest build
```

This repository has not been deployed by its setup script. Production and preview deployment checks must be performed through Workers Builds.

## References

- [Official cf starter](https://github.com/cloudflare/cf/tree/main/packages/cli/src/commands/init)
- [cf releases](https://github.com/cloudflare/cf/releases)
