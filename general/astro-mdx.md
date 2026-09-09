# Astro + MDX

Use for projects built with Astro and MDX. Read the installed versions, configuration, content schemas, and existing components before changing the stack. Use documented patterns for those versions rather than copying a recipe's dependencies or flags.

## Rendering boundaries

Keep content and layout server-rendered by default. Hydrate only interactive UI framework components, choosing a `client:*` directive for when interactivity is needed. Astro components themselves have no hydration runtime. Use browser scripts or an existing framework island rather than adding a framework for a small interaction.

Separate build/server frontmatter from browser code. Keep DOM-dependent imports and initialization out of server execution. Pass supported serializable props across hydration boundaries, not functions, DOM nodes, or secrets. Use `client:only` only when skipping server rendering is justified, with useful fallback content.

## MDX and content

Write `.mdx` in MDX/JSX syntax, not `.astro` syntax. Reuse content schemas, layouts, and component mappings; preserve frontmatter, headings, anchors, and accessibility semantics.

Check the configured Markdown processor before adding plugins. Do not assume remark, rehype, or recma options work with every Astro processor or version. Preserve existing Markdown/MDX configuration inheritance deliberately.

Treat MDX as executable content. Keep authored MDX trusted; do not evaluate untrusted strings as MDX or pass them through raw HTML insertion. Use validated data in trusted components for user-supplied content.

## Browser lifecycle and completion

Initialize browser features only after their elements exist. If client routing is enabled, use its navigation lifecycle, such as `astro:page-load`, instead of relying only on `DOMContentLoaded`. Make initialization idempotent and release removed components' observers, listeners, and chart instances without destroying intentionally persisted components.

Check affected MDX pages, server rendering, client interaction, and repeated navigation where applicable. Verify the production build and client bundle relevant to the change; a working dev page does not establish correct hydration or bundling.

References: [MDX integration](https://docs.astro.build/en/guides/integrations-guide/mdx/), [framework components](https://docs.astro.build/en/guides/framework-components/), [navigation lifecycle](https://docs.astro.build/en/guides/view-transitions/).
