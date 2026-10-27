---
name: react-performance
description: React and Next.js performance rules (adapted from Vercel's React Best Practices), ordered by impact - request waterfalls, bundle size, server-side work, client fetching, re-renders, rendering, JS micro-optimizations. Use when writing, reviewing or refactoring React/Next.js code for speed, diagnosing slow loads or interactions, or fixing Core Web Vitals (LCP, INP, CLS) and bundle-size regressions.
---

# React performance

Work top-down: fix the CRITICAL categories before micro-optimizing. The full catalogue with examples is in [references/rules.md](references/rules.md).

| Priority | Category | Typical fix |
| --- | --- | --- |
| 1 CRITICAL | **Waterfalls** | `Promise.all` independent awaits; start promises early, await late; cheap sync checks before `await`; split Server Components so siblings fetch in parallel; `<Suspense>` close to slow data |
| 2 CRITICAL | **Bundle size** | no barrel imports (or `optimizePackageImports`); `next/dynamic` for heavy client-only parts; third-party scripts via `next/script` `lazyOnload`; conditional `import()` |
| 3 HIGH | **Server** | authenticate and authorize inside every Server Action; `React.cache` per request; cache cross-request data; pass minimal props to Client Components; no mutable module state; `after()` for non-blocking work |
| 4 MED-HIGH | **Client fetching** | SWR/TanStack Query for shared data; one shared listener per event; passive scroll listeners |
| 5 MEDIUM | **Re-renders** | derive during render (not `useEffect`); select derived booleans from stores; stable default props; primitive deps; `startTransition`/`useDeferredValue`; never define components inside components |
| 6 MEDIUM | **Rendering** | `content-visibility: auto` for long lists; animate wrappers, not SVGs; ternary over `&&` with numbers; narrow `suppressHydrationWarning`; reserve space to avoid CLS |
| 7 LOW-MED | **JS** | `Map`/`Set` lookups, hoisted RegExp, single-pass loops |
| 8 LOW | **Advanced** | `useEffectEvent`, handler refs |

## How to use

1. Measure first: Lighthouse / Web Vitals in the field, `@next/bundle-analyzer`, React DevTools Profiler.
2. Map the symptom: LCP points at waterfalls, bundle size and resource hints; INP at re-renders, rendering and JS; CLS at layout reservation and Suspense placement.
3. Fix the highest-priority category that applies, then measure again.
4. If the project uses **React Compiler**, treat manual `useMemo`/`useCallback` advice as review-only.

Report findings as: file:line, rule, impact (estimated), fix.
