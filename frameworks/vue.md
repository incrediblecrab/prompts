# Vue

Use for Vue applications. Inspect installed Vue major/minor, compiler, TypeScript, build tooling, router/store, and SSR configuration. Match the existing Options or Composition API; apply Vue 3 syntax only where supported. Do not infer Nuxt, upgrade Vue, or switch renderers incidentally.

## Component contracts and ownership

Prefer SFCs and `<script setup lang="ts">` in Vue 3 projects already using Composition API and TypeScript. Type props, emitted events, and relevant slot or `v-model` contracts with supported APIs. Keep props read-only, including nested data by convention; let their owner update state through explicit events. Avoid mirrored prop state unless deliberately modeling a draft/reset boundary.

Use stable primitive `:key` values for reorderable items, not array positions or random values. Preserve semantic controls, labels, keyboard interaction, and focus.

## Reactivity and derivation

Use refs or reactive objects deliberately; access refs with `.value` in JavaScript and respect template unwrapping limits. Do not replace a `reactive` object's root or destructure primitive properties and expect tracking to survive.

Distinguish that rule from compiler-assisted props destructuring: `defineProps` destructuring is reactive by default in Vue 3.5+ within the same `<script setup>`. On older versions keep `props.x` or use `toRef`/`toRefs`. Pass getters or refs, not snapshots, to watchers and composables. Keep computed getters pure and synchronous; use watchers for side effects.

## Watchers and disposal

Choose explicit `watch` sources when dependency control matters; `watchEffect` tracks only reads before the first `await`. Cancel obsolete requests and suppress stale completions. Register invalidation cleanup through the callback's `onCleanup` argument. If using Vue 3.5+ `onWatcherCleanup`, call it synchronously before any `await`.

Create setup watchers synchronously for automatic component teardown. Explicitly stop asynchronously created watchers and release owned listeners, timers, subscriptions, and observers.

## Rendering and completion

When SSR is configured, create the application and any router/store instances per request; never store user-specific mutable state in module singletons. Keep server/client initial markup consistent. Defer DOM-dependent imports and initialization to `onMounted` or the existing client lifecycle; unmount hooks do not run during SSR.

Verify the installed release's Vapor support and stability; never assume a preview renderer is stable or default. Run configured SFC type checks, focused behavior tests, and the production build; bundler transpilation alone is insufficient. Verify prop/event behavior, rapid async changes, unmounting, navigation/back behavior, and hydration where applicable.

Reference review: September 9, 2026.

References: [SFC script setup](https://vuejs.org/api/sfc-script-setup.html), [reactivity fundamentals](https://vuejs.org/guide/essentials/reactivity-fundamentals.html), [props](https://vuejs.org/guide/components/props.html), [watchers](https://vuejs.org/guide/essentials/watchers.html), [SSR](https://vuejs.org/guide/scaling-up/ssr.html), [TypeScript checks](https://vuejs.org/guide/typescript/overview.html), [release notes](https://github.com/vuejs/core/releases).
