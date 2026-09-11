# Angular

Use for Angular applications, not AngularJS. Check installed Angular/CLI, TypeScript, RxJS, and Node versions against the compatibility matrix. Inspect `angular.json`, bootstrap providers, routing, forms, and tests before choosing APIs. Follow the installed release and preserve the configured architecture.

## Components and templates

Prefer standalone components for new code where supported, while retaining existing NgModules and provider scopes. Keep component contracts typed and template imports explicit. Use supported `@if`, `@for`, and `@switch` patterns consistently with nearby code; track reorderable items by stable identity. Preserve semantic controls, labels, keyboard behavior, and focus.

## State and lifetimes

Use signals for owned synchronous state and pure `computed` derivations. Reserve `effect` for non-reactive integrations, not copying derived state. Keep RxJS for streams, cancellation, and concurrency. Reuse `toSignal` conversions; use `AsyncPipe` or `takeUntilDestroyed` with the correct `DestroyRef`, or explicit teardown on older versions.

Match effects and subscriptions to their owner's lifetime. Register effect cleanup for reruns/destruction; release listeners, timers, and pending work. Verify resource stability per version: `resource`, `rxResource`, and `httpResource` are stable since v22.0. Use resources for reads, honor cancellation, and keep mutations explicit.

## Change detection and forms

Inspect actual providers and build/test polyfills. Zoneless is default in v21+, but `provideZoneChangeDetection` overrides it; `OnPush` alone does not enable zoneless. Notify Angular through template-consumed signals, `AsyncPipe`, or `markForCheck`, including programmatic reactive-form updates where necessary.

Preserve the form strategy. Prefer typed reactive forms for established validation workflows, respecting nullability, reset semantics, and disabled values. Signal Forms' `form` is experimental in v21 and stable since v22.0; verify each newer API separately. Do not rewrite forms or remove ZoneJS incidentally.

## Rendering and verification

Respect configured CSR, SSR, prerendering, and hydration. Defer DOM-dependent imports and work to browser execution, using supported `afterNextRender` hooks where appropriate. Keep initial markup deterministic; do not branch templates on browser detection or mutate DOM before hydration.

Run focused component/form tests, configured template/type checks, and the affected production build. Exercise loading/errors, asynchronous updates, teardown, and navigation. Check SSR hydration when enabled; match tests to production change detection rather than hiding missed notifications with forced detection.

Reference review: September 9, 2026.

References: [Version compatibility](https://angular.dev/reference/versions), [signals and effects](https://angular.dev/guide/signals/effect), [zoneless](https://angular.dev/guide/zoneless), [typed forms](https://angular.dev/guide/forms/typed-forms), [Signal Forms API](https://angular.dev/api/forms/signals/form), [resource API](https://angular.dev/api/core/resource), [SSR](https://angular.dev/guide/ssr).
