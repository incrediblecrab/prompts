# Swift

Use for Swift packages, server/CLI code, and Apple-platform apps. Read the installed compiler/toolchain, per-target Swift language mode, `Package.swift` tools version, SDK, minimum deployment targets, and build settings separately. A newer compiler does not automatically select Swift 6 language mode. Distinguish release toolchains from development snapshots.

## Ownership and errors

Prefer immutable value types where identity is unnecessary; use classes or actors for deliberate shared identity. Make resource lifetimes and capture ownership explicit; use weak references for actual cycles, not reflexively.

Represent absence with optionals and recoverable failures with throwing APIs or the existing result type. Preserve error context; do not hide failures with `try?`, force unwraps, or `try!`.

## Isolation and tasks

Protect shared mutable state with actors or an established synchronization boundary. Verify `Sendable` requirements at crossings; fix ownership or isolation instead of adding unchecked conformances or unsafe sendability casts.

Inspect default actor isolation and upcoming-feature settings per target. Swift 6.2 introduced configurable main-actor defaults and `NonisolatedNonsendingByDefault`, under which nonisolated async functions inherit the caller's isolation. Other configurations can switch executors. Neither `async` nor `nonisolated` means background execution. For expensive async work, use a supported explicit boundary such as `@concurrent` in Swift 6.2+; `Task {}` can inherit the actor and is not an offloading guarantee.

Prefer structured `async let` or task groups. Own and cancel unstructured tasks when needed, check cooperative cancellation, and revalidate state after suspension; actor isolation does not make an entire async operation atomic.

## Platform and UI boundaries

Check SDK and deployment availability; use `#available` and conditional compilation where appropriate. Preserve memory ownership and callback isolation across C/Objective-C/C++ interfaces. Resume checked continuations exactly once, and cross to `MainActor` for UI updates rather than assuming a callback's thread proves actor isolation.

Only for SwiftUI, match observation and state ownership to supported OS versions. Use `@Observable` where supported and appropriate; preserve supported `ObservableObject` patterns for existing targets. Keep `body` side-effect-free, tie loading to view lifecycle/identity, and handle cancellation and stale results.

## Focused checks

Run the affected SwiftPM target/product build and filtered `swift test`, or the relevant Xcode scheme, destination, and test plan with `xcodebuild`. Preserve configured diagnostics and dependency resolution. Cover failure, cancellation, isolation, and supported deployment paths; do not treat a host-only package build as Apple-platform validation.

Reference review: September 9, 2026.

References: [language modes and migration](https://www.swift.org/migration/documentation/migrationguide/), [Swift 6.2 concurrency](https://www.swift.org/blog/swift-6.2-released/), [concurrency](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/concurrency/), [nonisolated async execution](https://docs.swift.org/compiler/documentation/diagnostics/nonisolated-nonsending-by-default/), [Observation migration](https://developer.apple.com/documentation/swiftui/migrating-from-the-observable-object-protocol-to-the-observable-macro), [SwiftPM commands](https://docs.swift.org/swiftpm/documentation/packagemanagerdocs/), [Xcode testing](https://developer.apple.com/documentation/xcode/running-tests-and-interpreting-results).
