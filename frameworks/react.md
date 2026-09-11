# React

Use for React components and applications. Inspect installed React, renderer, host framework, compiler, Hooks lint configuration, and existing data layer. Use APIs documented for those versions and that host; do not assume Next.js, Server Components, or a dependency upgrade.

## Own state and identity

Keep render calculations pure; treat props and state as immutable snapshots. Keep state with its closest owner, lift only shared state, and derive values instead of mirroring props. Use functional state updates when depending on previous state.

Define component functions at module scope and use stable data keys. Preserve component type and tree identity when state should survive; change keys deliberately for resets. Follow documented Hook call rules.

## Synchronize with Effects

Calculate derived data during render and handle user-triggered work in event handlers or supported Actions. Reserve Effects for external-system synchronization. Declare reactive dependencies and fix their cause rather than disabling lint checks.

Pair subscriptions, timers, observers, and connections with cleanup. Abort obsolete requests where possible and ignore stale completions so earlier responses cannot overwrite newer state. Make setup-cleanup-setup safe under development Strict Mode; do not mask checks with run-once refs.

Where installed React and lint tooling support `useEffectEvent`, use it only for non-reactive events fired from Effects. Keep Effect Events local; never use them to hide required dependencies.

## Schedule and optimize deliberately

Keep controlled-input updates urgent. Use supported transitions for non-urgent rendering, not as request cancellation or debouncing. For async transitions, follow the installed API's post-`await` rules; wrap subsequent state updates in `startTransition` where required.

When useful and supported, wire `useActionState` through form Actions or an explicit transition. Respect its previous-state argument, expose pending and expected-error states, and handle unexpected failures. Client Actions do not require Server Actions.

Check whether React Compiler is actually enabled. Rely on its memoization for newly compiled code; otherwise profile before adding `memo`, `useMemo`, or `useCallback`. Preserve existing memoization unless a tested change justifies removal. Never depend on memoization for correctness.

## Respect the host and verify behavior

Apply server/client boundaries only when the host supports them. For server rendering and hydration, ensure server markup matches the first client render and keep browser-only access out of server execution.

Test visible behavior with the existing harness: keyboard and form flows, pending/error states, rapid updates, out-of-order responses, state preservation/reset, and teardown. Check hydration where relevant, and run related lint/build checks rather than asserting exact render counts.

Reference review: September 9, 2026.

References: [state identity](https://react.dev/learn/preserving-and-resetting-state), [Effects and cleanup](https://react.dev/learn/synchronizing-with-effects), [Effect Events](https://react.dev/reference/react/useEffectEvent), [transitions](https://react.dev/reference/react/startTransition), [Action state](https://react.dev/reference/react/useActionState), [Compiler and memoization](https://react.dev/learn/react-compiler/introduction), [hydration](https://react.dev/reference/react-dom/client/hydrateRoot).
