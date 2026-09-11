# Next.js

Use for Next.js applications. Inspect installed `next`, `react`, and `react-dom`, lockfiles, `next.config.*`, route directories, build scripts, and deployment target. Follow version-matched documentation, including bundled docs when available; do not mandate upgrades or router migrations.

## Match the router and runtime

Preserve existing App Router, Pages Router, or mixed ownership. Keep `getStaticProps`, `getServerSideProps`, and API Routes in `pages`; do not transplant them into `app`.

Match Node.js and runtime APIs to the installed release and deployment adapter. Resolve `cookies()`, `headers()`, `draftMode()`, route `params`, and page `searchParams` asynchronously where required. Next.js 15's temporary synchronous compatibility is removed in 16.

## Protect execution boundaries

Keep App Router pages and layouts as Server Components by default, with narrow `"use client"` boundaries for interactivity. Client Components also prerender on the server; keep browser-only access out of prerendering. Pass minimal React-serializable props, not arbitrary functions or secrets. Mark server-only modules and keep secrets out of `NEXT_PUBLIC_*`.

Treat Server Actions and Route Handlers as callable endpoints. Validate untrusted inputs and authenticate and authorize each protected operation against the specific resource. UI visibility, page checks, and action IDs are not authorization.

## Make caching explicit

Check `fetch`, Route Handler, prerendered output, and client navigation caching separately for the installed model. Default uncached fetch behavior does not mean all route output is dynamic.

Treat `cacheComponents` and `"use cache"` as opt-in capabilities, not universal defaults; Cache Components requires Node.js. With it enabled, use Suspense around uncached or request-dependent UI. Read cookies and headers outside shared cache scopes; if caching personalized data, authorize first and scope keys to user/tenant. Set cache lifetimes deliberately and prevent cross-user reuse.

After successful mutations, invalidate affected paths or tags with supported APIs. Distinguish `revalidateTag(tag, 'max')` stale-while-revalidate from Server Action-only `updateTag` for immediate read-your-writes where available. Do not mistake router refresh for data-cache invalidation.

## Verify routing and production behavior

Use `Link` and router-matched navigation: `next/navigation` for App Router, `next/router` for Pages Router. Follow existing loading, error, and not-found conventions; App Router `error.*` boundaries are Client Components. Do not swallow redirect or not-found control flow.

Run production build/start or deployment-equivalent checks. Exercise direct loads, client navigation, pending/error recovery, unauthorized mutations, personalized requests, and freshness after revalidation. A successful development render does not verify production caching.

Reference review: September 9, 2026.

References: [version 16 contracts](https://nextjs.org/docs/app/guides/upgrading/version-16), [component boundaries](https://nextjs.org/docs/app/getting-started/server-and-client-components), [Cache Components configuration](https://nextjs.org/docs/app/api-reference/config/next-config-js/cacheComponents), [caching models](https://nextjs.org/docs/app/getting-started/caching), [Route Handlers](https://nextjs.org/docs/app/getting-started/route-handlers), [data security](https://nextjs.org/docs/app/guides/data-security), [navigation and refresh](https://nextjs.org/docs/app/api-reference/functions/use-router).
