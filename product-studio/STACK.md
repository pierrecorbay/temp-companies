# Product Studio — Preferred Technical Stack

This file is the canonical stack reference for Product Studio. All agents read it before making technology or architecture decisions. Deviations from the defaults require explicit approval and must be documented in `memory/decisions.md`.

---

## Web Stack (default)

### Framework — Next.js 15 App Router

- Use the App Router (`app/`) exclusively. Do not use the Pages Router (`pages/`).
- Server Components by default; add `"use client"` only when necessary (event handlers, browser APIs, hooks).
- Route Handlers (`app/api/`) for API endpoints. Avoid creating separate Express/Hono servers unless the use case is clearly outside Next.js scope.
- **find-docs trigger:** Always run `/find-docs` for Next.js before implementing middleware, auth callbacks, server actions, or caching behavior — these APIs change across minor versions.

### Backend — Convex

- Convex is the database, backend functions, real-time subscriptions, and file storage layer. Do not add a separate ORM or REST API layer on top.
- All data access goes through Convex queries and mutations. No raw SQL.
- Schema defined in `convex/schema.ts`. All tables typed. Validators on all mutation arguments.
- Real-time queries via `useQuery` on the client; background jobs via Convex scheduled functions (`ctx.scheduler`).
- **find-docs trigger:** Always run `/find-docs` for Convex before writing mutations, validators, scheduled functions, or file storage calls. The API surface evolves quickly.

### Auth — Better Auth

- Better Auth handles sessions, OAuth providers, and role-based access.
- Session data exposed via `auth.api.getSession()` server-side; `useSession()` client-side.
- Do not roll custom session management or JWT handling.
- **find-docs trigger:** Run `/find-docs` for Better Auth before implementing any OAuth provider, session plugin, or access control policy.

### Styling — Tailwind CSS + shadcn/ui

- Tailwind for all utility styling. No styled-components, no CSS modules (except for complex animations).
- shadcn/ui for component primitives. Add components via `npx shadcn@latest add <component>`, not by writing primitives from scratch.
- Design tokens from DESIGN.md must map to Tailwind config (`tailwind.config.ts`). Never use raw hex values inline — always use token-mapped classes.

### Deployment — Vercel (app) + Cloudflare (services)

- **App host**: Vercel. Zero-config for Next.js. Use Vercel for the primary app deployment.
- **CDN / DNS**: Cloudflare. Point the domain to Vercel via Cloudflare proxy.
- **Storage**: Cloudflare R2 for large file/asset storage (cheaper than S3 at scale).
- **Bot protection**: Cloudflare Turnstile for CAPTCHA when needed.
- **Do NOT** deploy the Next.js app itself to Cloudflare Workers/Pages — edge runtime limitations (`no Node.js APIs`, `no native modules`) cause agent bugs and require constant workarounds.
- Environment variables managed in Vercel dashboard and committed to `convex/.env.local` (Convex-specific).

---

## Mobile Stack (default)

### Framework — Expo (React Native)

- Expo is the default for all mobile work. Do not start with bare React Native unless Expo's managed workflow cannot support a required native module.
- Use Expo Router (`app/`) for navigation — same file-based routing convention as Next.js App Router.
- **find-docs trigger:** Run `/find-docs` for Expo before using any native module, EAS Build configuration, or Expo SDK API.

### Backend — Convex (same as web)

- Use the same Convex backend for mobile. The `convex-react-native` package provides `useQuery` and `useMutation` hooks identical to the web SDK.
- One schema, one set of mutations, one set of queries — shared across web and mobile. Do not create a separate mobile-specific backend.
- **This is the primary reason to use Expo over Flutter**: a Flutter app cannot share Convex functions without a separate REST wrapper layer.

### Auth — Better Auth

- Better Auth supports React Native via the `@better-auth/expo` package.
- Session persistence via Expo SecureStore.

### In-App Purchases — RevenueCat

- RevenueCat is the standard for all in-app purchases and subscriptions. Do not implement StoreKit or Google Play Billing directly.
- Use `react-native-purchases` (RevenueCat's React Native SDK).
- Entitlements defined in RevenueCat dashboard — do not hardcode product IDs.
- **find-docs trigger:** Run `/find-docs` for RevenueCat before implementing any purchase flow, entitlement check, or paywall.

### Styling — NativeWind

- NativeWind brings Tailwind utility classes to React Native. Use it for all styling to keep conventions consistent with the web codebase.
- Design tokens from DESIGN.md must map to the NativeWind config.

### Deployment — Expo EAS Build + App Store / Google Play

- EAS Build for CI/CD. EAS Submit for store submissions.
- OTA updates via Expo Updates for JS-only changes (no native code changes).

---

## Shared Conventions

### Language — TypeScript (strict)

- TypeScript strict mode everywhere (`"strict": true` in tsconfig).
- No `any` without a comment explaining why. Prefer `unknown` for external inputs.
- Shared types between web and mobile in a `packages/shared` workspace (if monorepo) or `convex/_generated/` types (always available from Convex).

### Validation — Zod

- All external inputs validated with Zod before use: API route bodies, form submissions, environment variables, Convex mutation arguments.
- Convex validators (`v.string()`, `v.object()`, etc.) for schema enforcement server-side.
- Zod schema = the single source of truth for input shapes. Do not duplicate with TypeScript interfaces.

### One Convex schema for both platforms

- `convex/schema.ts` is the single source of truth for the data model.
- Tables, indexes, and validators defined once. Both web and mobile read/write through the same functions.
- New tables require a schema migration plan documented in `memory/decisions.md`.

---

## Decision Rules — When to Deviate

| Scenario | Approved deviation | Notes |
|---|---|---|
| iOS-only product requiring ARKit, Core ML, or Live Activities | Native Swift | Document in decisions.md. Expo cannot support these. |
| iOS-only premium utility where native feel IS the product | Native Swift | Document in decisions.md with justification. |
| Android-only or cross-platform with deep device integration | Flutter | Only if Expo native modules cannot cover the requirement. |
| High-throughput background jobs that exceed Convex limits | Separate service (Railway / Fly.io) | Keep Convex for user-facing data; add a worker for heavy processing. |
| Edge API routes that truly benefit from low latency | Cloudflare Workers (isolated route) | Only for specific routes, not the entire app. Document why. |
| Self-hosted requirement (enterprise B2B, not B2C) | Postgres + Prisma on Railway | B2C products default to Convex. |

Any deviation must be:
1. Discussed in the CEO brief or CTO technical plan
2. Recorded in `memory/decisions.md` with the decision owner, scope, and reasoning
3. Referenced in `STACK.md` under this section

---

## Agent Guidance

### find-docs is required before these operations

| Operation | Library to look up |
|---|---|
| Next.js middleware, server actions, caching | `next` |
| Convex mutations, validators, scheduled functions, file storage | `convex` |
| Better Auth OAuth providers, session plugins, access control | `better-auth` |
| shadcn/ui component installation or customization | `shadcn-ui` |
| Expo SDK native modules, EAS Build config | `expo` |
| RevenueCat purchase flows, entitlement checks | `revenuecat` |
| NativeWind theming, Tailwind config for RN | `nativewind` |

### Patterns agents commonly get wrong

- **Next.js**: Using `getServerSideProps` (Pages Router pattern) instead of async Server Components. Using `useRouter` from `next/navigation` instead of `next/router` in App Router. Forgetting `"use server"` on server actions.
- **Convex**: Calling `ctx.db.get()` inside a query without handling `null`. Missing `v.` validators on mutation arguments. Using `ctx.runMutation` inside a query (not allowed).
- **Better Auth**: Forgetting to set `BETTER_AUTH_SECRET` in env. Calling `auth.api.getSession()` from a client component (must be server-side).
- **RevenueCat**: Calling `Purchases.getOfferings()` before `Purchases.configure()`. Not handling the `CustomerInfo` null case on first launch.
