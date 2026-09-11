# Rust

Use for Rust libraries, services, CLI tools, and embedded or FFI components. Read the installed toolchain, `rust-toolchain.toml`, Cargo manifests, lockfile, target configuration, and CI. Distinguish stable, beta, and nightly from each crate's edition and declared `rust-version` minimum supported Rust version (MSRV); preserve those contracts.

## Compatibility and dependencies

Use syntax and APIs supported by the selected compiler and MSRV. Rust 2024 is a stable edition, available since Rust 1.85; do not change the edition, MSRV, or channel incidentally. Keep nightly-only features within the project's existing nightly policy.

Read the workspace resolver explicitly, including virtual workspaces; member editions do not independently select it. Respect additive feature unification. Add only needed dependencies and features, inspect transitive/default features, and preserve lockfile policy. Resolver fallback is not proof of MSRV compatibility.

## Ownership and failure boundaries

Model ownership and lifetimes before adding `clone`, `Rc`, or `Arc<Mutex<_>>` to satisfy the borrow checker. Borrow when appropriate, move when ownership transfers, and use RAII for resource cleanup.

Return meaningful `Result` errors for recoverable failures; preserve context and sources. Reserve panics, `unwrap`, and `expect` for documented invariants consistent with the project's panic policy.

Keep `unsafe` small and justify each operation's validity, alignment, initialization, aliasing, lifetime, and synchronization invariants. Expose safe wrappers only when callers cannot violate them. At FFI boundaries, verify ABI/layout, allocation ownership, callback lifetimes, and permitted unwinding; do not assume `catch_unwind` catches aborts or foreign exceptions.

## Async and synchronization

Reuse the chosen async runtime. Offload blocking I/O and CPU-heavy work through its documented facilities; `async` alone does not prevent executor starvation. Bound concurrency and observe spawned-task failures.

Keep critical sections short. Do not hold blocking lock guards across `.await`; justify async guards that span suspension. Design cancellation and shutdown for partial operations and cleanup. Check future-drop and task-handle semantics rather than assuming that dropping a handle cancels work.

## Focused checks

Use existing formatting and lint configuration. When available, run package-scoped `cargo fmt -p <package> -- --check` and `cargo clippy -p <package>`; report missing components without installing them or changing toolchains. Run focused `cargo test -p <package>` selectors, relevant doctests, and `cargo check` for affected target triples and supported feature combinations. Test the declared MSRV when compatibility is affected. Do not substitute blanket `--all-features` for meaningful default, minimal, and platform-specific checks.

Reference review: September 9, 2026.

References: [Rust 2024](https://doc.rust-lang.org/edition-guide/rust-2024/index.html), [MSRV](https://doc.rust-lang.org/cargo/reference/rust-version.html), [dependency resolution](https://doc.rust-lang.org/cargo/reference/resolver.html), [unsafe contracts](https://doc.rust-lang.org/reference/behavior-considered-undefined.html), [FFI boundaries](https://doc.rust-lang.org/nomicon/ffi.html), [async execution and cancellation](https://rust-lang.github.io/async-book/part-guide/more-async-await.html), [Cargo tests](https://doc.rust-lang.org/cargo/commands/cargo-test.html).
