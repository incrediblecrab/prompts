# TypeScript

Use for TypeScript applications, libraries, and tooling. Inspect the installed compiler, lockfile, effective `tsconfig` inheritance, project references, runtime, and build pipeline before changing code or configuration.

## Compiler and configuration

Separate compiler support from framework, editor, linter, and generator compatibility. TypeScript 7.0 is the released native compiler, but does not expose the programmatic compiler API used by many integrations. Check each tool's supported versions and the documented TypeScript 6 compatibility path before replacing the toolchain. Do not treat old `tsgo` preview installation instructions as the current stable setup.

Check migration notes for changed defaults and removed options. TypeScript 7.0 defaults `types` to `[]` and `rootDir` to `.`, and removes `baseUrl`; preserve intended globals, output paths, and runtime support when migrating. Do not upgrade the compiler as a side effect of an unrelated task.

## Types and trust boundaries

Model meaningful states with precise types and discriminated unions. Prefer inference and constrained generics over elaborate type machinery. Use narrowing and exhaustive handling instead of `any`, double assertions, or non-null assertions that merely suppress uncertainty.

Treat external data as untrusted until runtime checks establish its shape and invariants. Type annotations, assertions, and `satisfies` do not validate input at runtime. Reuse the project's validation mechanism and surface invalid data through its normal error contract.

Preserve strictness. Distinguish absent properties, explicit `undefined`, and failed indexed lookups when the domain requires it. Evaluate additional options such as `noUncheckedIndexedAccess` deliberately rather than turning a local change into a project-wide migration.

## Modules and emitted code

Match `module` and `moduleResolution` to the actual runtime or bundler, including package exports, ESM/CommonJS boundaries, and required file extensions. A bundler resolving an import does not prove that directly emitted Node.js code will resolve it.

Use explicit type-only imports and exports where appropriate, respecting `verbatimModuleSyntax` and required side-effect imports. TypeScript `paths` mappings do not rewrite emitted import specifiers; keep runtime, bundler, and test-runner resolution aligned. Check emitted syntax and runtime APIs separately; type declarations do not supply polyfills.

## Completion

Run the project's actual type-check command with its intended configuration or project-reference build. Successful transpilation, type stripping, or a dev-server start is not a type check. Check runtime behavior at changed data and module boundaries as well.

For libraries, verify generated declarations, package entry points, and a representative supported consumer. Do not hide regressions with broad diagnostic suppressions or weaker compiler settings.

Reference review: September 9, 2026.

References: [TypeScript 7.0 release and compatibility](https://devblogs.microsoft.com/typescript/announcing-typescript-7-0/), [narrowing](https://www.typescriptlang.org/docs/handbook/2/narrowing.html), [module theory](https://www.typescriptlang.org/docs/handbook/modules/theory.html), [path mappings](https://www.typescriptlang.org/tsconfig/paths.html), [verbatim module syntax](https://www.typescriptlang.org/tsconfig/verbatimModuleSyntax.html), [optional properties](https://www.typescriptlang.org/tsconfig/exactOptionalPropertyTypes.html), [indexed access](https://www.typescriptlang.org/tsconfig/noUncheckedIndexedAccess.html).
