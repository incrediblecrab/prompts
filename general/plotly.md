# Plotly

Use for Plotly.js in JavaScript or TypeScript applications. Follow the installed version, existing wrapper, design system, and data contract. Do not assume Python or Dash APIs apply to Plotly.js.

## Choose the runtime

Use the smallest existing or documented bundle that supports the required trace types and features. The basic bundle is not the full library. Respect project bundle constraints, and verify required traces in the production artifact before changing distributions.

Load DOM-dependent Plotly code in the browser, after a correctly sized container exists. Keep server rendering safe and provide useful static or textual content before an interactive chart loads.

## Create, update, and dispose

Give each chart one owner and one container. Initialize once, then use `Plotly.react` or an appropriate incremental API instead of repeatedly replacing the plot with `newPlot`.

For `Plotly.react`, replace changed data arrays immutably or update `layout.datarevision`. Use a stable, truthy `uirevision` when compatible updates should preserve user interactions; change it deliberately when the view should reset.

Respond to container size changes, not only window resizing. Avoid resize loops, zero-size renders, duplicate event handlers, and late asynchronous updates after disposal. On actual teardown, call `Plotly.purge` and release application-owned listeners, observers, and pending work.

## Data and output

Keep data, layout, and config typed according to the installed API. Validate trace shapes, paired arrays, numeric/date values, units, and missing-data handling. Distinguish an empty dataset from an invalid one; do not silently turn missing values into zero.

Use readable labels, intentional colors, sources, and an accessible description or data alternative. Preserve useful interaction controls. A polished chart must not imply more than the data supports.

Check first render, representative updates, intended zoom/selection persistence, resize, and teardown. Test the actual shipped bundle. Surface rendering failures through the application's normal error path rather than leaving an unexplained blank container.

References: [function reference](https://plotly.com/javascript/plotlyjs-function-reference/), [bundle inventory](https://github.com/plotly/plotly.js/blob/master/dist/README.md), [UI persistence](https://plotly.com/javascript/uirevision/).
