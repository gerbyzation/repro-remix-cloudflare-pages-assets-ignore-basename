# Repro cloudflare pages assets serving ignoring base(name)

Remix supports the `basename` setting now, along with vite's `base` this should
allow you to serve an app (including all assets) from a basename other
than `/` (e.g. `/admin`). However despite setting the base
the build still writes files to `/assets` and the cloudflage pages integration
does not remove the base when reading assets, resulting in 404.

Repro steps:

1. `pnpm install`
2. `pnpm build`
3. `pnpm start`
4. visit `http://localhost:8788/my-basename`. The static files will 404
