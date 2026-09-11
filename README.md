# Prompt blocks

Reusable Markdown instructions for general work and academic research. Use one block on its own or combine the two or three a task needs. Each governs its stated scope; `core` and `preset-v1` are optional, not prerequisites.

Blocks are organized in `presets/`, `general/`, `frameworks/`, and `academia/`. Worked examples live in `example/`. The files contain instructions, not executable agents or a framework to install.

## Presets

Optional persona, audience, and thinking preferences. Use a preset with whichever task-specific blocks are relevant.

| Block | Use |
| --- | --- |
| [preset-v1](presets/preset-v1.md) | MIT/Stanford professor persona, named expert audiences, and scalable/modular/KISS/MECE thinking. |

## General

Shared working, writing, documentation, and evidence guidance. General blocks can also support academic work.

| Block | Use |
| --- | --- |
| [core](general/core.md) | Scope, autonomy, evidence, and honest completion. |
| [bary](general/bary.md) | Central supervision, worker isolation, progress deadlines, containment, and safe handoffs. |
| [editorial](general/editorial.md) | Precise prose, readable structure, and proportionate editing. |
| [documentation](general/documentation.md) | Reader tasks, Diataxis, canonical sources, and stable navigation. |
| [sources](general/sources.md) | Primary evidence, citations, retrieval limits, acceptance checks, and valid measurements. |

## Frameworks

Framework, language, and rendering-library implementation guidance. Select the blocks that match the project's actual stack.

| Block | Use |
| --- | --- |
| [Angular](frameworks/angular.md) | Component architecture, signals and RxJS, change detection, forms, and hydration. |
| [Astro + MDX](frameworks/astro-mdx.md) | Rendering boundaries, version-aware MDX configuration, and navigation lifecycle. |
| [D3](frameworks/d3.md) | DOM ownership, keyed joins, data/scales, responsive layout, and lifecycle cleanup. |
| [Next.js](frameworks/next.md) | Router and runtime boundaries, caching, request data, and server mutations. |
| [Plotly](frameworks/plotly.md) | Trace-compatible bundles, efficient updates, UI state, resizing, and cleanup. |
| [React](frameworks/react.md) | Component identity, state and effects, async interactions, and rendering boundaries. |
| [Rust](frameworks/rust.md) | Toolchains and editions, ownership, unsafe invariants, async execution, and Cargo checks. |
| [Swift](frameworks/swift.md) | Language modes, actor isolation, concurrency, availability, and target-specific checks. |
| [TypeScript](frameworks/typescript.md) | Compiler compatibility, runtime validation, module resolution, and declaration contracts. |
| [Vue](frameworks/vue.md) | Component contracts, reactive state, watcher cleanup, and SSR boundaries. |

## Academia

Mathematical investigation, formal proof, and computational discovery. These are independent blocks, not a mandatory three-stage pipeline.

| Block | Use |
| --- | --- |
| [mathematics](academia/mathematics.md) | Precise claims, counterexamples, proof development, and honest result status. |
| [formal proof](academia/formal-proof.md) | Preserving the theorem, checker-driven repair, and explicit proof assumptions. |
| [computational search](academia/computational-search.md) | Valid candidates, protected evaluators, bounded search, and reproducible artifacts. |

## Combine them

Supply the actual task, relevant inputs, intended audience, required output, and applicable constraints. Read or paste the selected files as separate sections. A link by itself does not load its contents unless the tool retrieves it.

Keep each block's rules within its scope. The task's required format and project-specific house rules specialize general style defaults; they do not relax evidence requirements, permissions, or higher-priority host instructions. Resolve a material conflict explicitly rather than relying on whichever paragraph appears last. One adequate check may satisfy several blocks; overlapping requirements do not require duplicate work.

Examples:

- `preset-v1` + `sources`: the usual persona and audience for source-backed analysis.
- `preset-v1` + `mathematics` + `sources`: mathematical work with the preset's calibration.
- `editorial` + `sources`: source-backed writing.
- `documentation` + `editorial`: reader-facing technical documentation.
- `core` + `bary` + `sources`: coordinated implementation with checked results.
- `astro-mdx` + `plotly`: a Plotly visualization embedded in Astro/MDX.
- `next` + `react` + `typescript`: a Next.js application using mutually supported React and TypeScript versions.
- `vue` + `typescript`: a Vue application with supported single-file component type checking.
- `d3` + `typescript`: a custom visualization in a typed codebase.
- `mathematics` + `sources`: conjectures, literature, and novelty claims.
- `formal-proof` + `sources`: proof-assistant work with explicit acceptance and trust requirements.
- `mathematics` + `computational-search` + `sources`: search for constructions or bounds and check the resulting artifacts.

Choose the renderer the task needs. Selecting both Plotly and D3 is not a requirement to use both, and they must not compete over the same chart nodes.

Use `bary` for substantial, independent branches, not as a prerequisite to every theorem or search.

Keep model and host configuration outside the reusable prose. Use the supported message roles and chat template, actual tool schemas, and documented reasoning or output controls. Deadlines, cancellation, write isolation, and hard budgets require host support; a prompt cannot enforce them by itself.

For reproducible use, read all selected files from the same repository commit.

## Example

[Applied Studies and Observations](example/example-applied-studies.md) is an intentionally broad example. It combines these five selected blocks, verbatim and in this order: `core`, `bary`, `editorial`, `documentation`, and `sources`. Project-specific requirements follow them.

The example uses an explicit selection, not every block in the library. It does not select the preset, implementation-specific blocks, or academia blocks. Dependency versions and validator counts come from the target project rather than fixed numbers in the prompt.

## Maintaining the library

This repository is the sole maintained source. Edit the Markdown here.

Work on version branches and merge completed versions into `main` with `--no-ff`. Update this index when adding, renaming, or regrouping a block.

When a selected block changes, reassemble the affected example from its declared selection in order, followed by its project context. Adding a library block does not automatically add it to an example.

## Review basis

Presets record personal working preferences. The original blocks were reviewed for September 8, 2026 using primary guidance and worked examples. The Angular, React, Rust, Swift, TypeScript, Next.js, and Vue blocks were reviewed against official documentation on September 9, 2026; their references and review dates appear in each file. The bary block was rewritten against the supervision references below on September 10, 2026.

General review references:

| Publisher | References |
| --- | --- |
| OpenAI | [Current prompting guidance](https://developers.openai.com/api/docs/guides/latest-model#prompting-best-practices), [per-run budget recipe](https://developers.openai.com/cookbook/articles/per_run_spending_controller_responses_api.md), [memory and compaction recipe](https://developers.openai.com/cookbook/examples/agents_sdk/building_reliable_agents_memory_compaction.md) |
| Anthropic | [Current prompting guidance](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices), [workflow recipes](https://github.com/anthropics/claude-cookbooks/blob/main/patterns/agents/basic_workflows.ipynb), [cost and quality optimization](https://github.com/anthropics/claude-cookbooks/blob/main/cost_optimization/cost_optimization.ipynb) |
| Hugging Face | [Agent cookbook](https://huggingface.co/learn/cookbook/multiagent_web_assistant), [chat templates](https://huggingface.co/docs/transformers/chat_templating) |
| Meta | [Llama 4 API recipe](https://github.com/meta-llama/llama-cookbook/blob/main/getting-started/build_with_llama_api.ipynb), [Prompt Ops](https://github.com/meta-llama/llama-prompt-ops) |
| DeepSeek | [R1 recommendations](https://github.com/deepseek-ai/DeepSeek-R1#usage-recommendations), [current thinking-mode and tool examples](https://api-docs.deepseek.com/guides/thinking_mode/) |
| Google | [Gemini prompting guidance](https://ai.google.dev/gemini-api/docs/prompting-strategies) |

Supporting references: [Diataxis](https://diataxis.fr/compass/), [arXiv API terms](https://info.arxiv.org/help/api/tou.html), and [W3C guidance for complex images](https://www.w3.org/WAI/tutorials/images/complex/).

Supervision references: [Temporal activity timeouts and heartbeats](https://docs.temporal.io/encyclopedia/detecting-activity-failures), [fencing tokens for stale writers](https://martin.kleppmann.com/2016/02/08/how-to-do-distributed-locking.html), [Claude Code scheduled tasks](https://code.claude.com/docs/en/scheduled-tasks), [goal-directed check-ins](https://code.claude.com/docs/en/goal), [background session isolation](https://code.claude.com/docs/en/agent-view), [subagent context isolation](https://code.claude.com/docs/en/agent-sdk/subagents), [OpenAI background mode](https://developers.openai.com/api/docs/guides/background), [OpenAI rate limits and backoff](https://developers.openai.com/api/docs/guides/rate-limits), and [Anthropic's multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system).

Implementation references: [Astro MDX](https://docs.astro.build/en/guides/integrations-guide/mdx/), [Astro component hydration](https://docs.astro.build/en/guides/framework-components/), [Plotly APIs](https://plotly.com/javascript/plotlyjs-function-reference/), [Plotly bundles](https://github.com/plotly/plotly.js/blob/master/dist/README.md), and [D3's official examples](https://d3js.org/getting-started).

Academic references: [Aletheia prompt examples](https://github.com/google-deepmind/superhuman/tree/main/aletheia), [DeepSeek-Prover-V2 template](https://github.com/deepseek-ai/DeepSeek-Prover-V2#5-quick-start), [Aristotle's query pipeline](https://arxiv.org/abs/2510.01346), [AlphaEvolve's experiment](https://github.com/google-deepmind/alphaevolve_repository_of_problems/blob/main/experiments/autocorrelation_problems/autocorrelation_problems.ipynb), [Axiom's statement contract](https://github.com/AxiomMath/PrimeGapsLib/blob/main/Challenge/Basic.lean), and [OpenAI's research workflow](https://openai.com/index/navier-stokes-solution/).

Recipes have model-specific assumptions and may be demonstrations rather than production implementations. These references are not a universal standard or evidence that this library has been benchmarked on every model.

Evaluate each block alone and representative two- and three-block combinations on the models and hosts you use. Compare task success and evidence quality alongside latency, tool calls, retries, and resource use. Keep a useful rule because it improves results, not because a provider or an older prompt happened to include it.
