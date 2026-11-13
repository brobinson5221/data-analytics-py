---
name: visualize-data
description: "Create quantitative charts and functional Sources inspectors, inline or in Data reports/dashboards. Use for meaningful trends, comparisons (including group trends that diverge from the overall result), distributions, uncertainty, relationships and standard chart interactions, or evidence whose scope/processing warrants inspection. Hand bespoke inline calculators, parameter-driven planning tools and interactive explainers to Visualize for UI and delivery. Skip plain prose, ordinary Markdown tables, simple arithmetic and file handoffs needing neither component."
---

# Visualize Data

Chart meaningful trends, comparisons, distributions, relationships, uncertainty and scenarios, even when the user has not explicitly asked for a chart. Use prose for a single value and a table for exact lookup; honor text-only and no-embed requests. Deliver requested reports and dashboards through [Build Report](../build-report/SKILL.md) or [Build Dashboard](../build-dashboard/SKILL.md). Conceptual diagrams use a separate workflow.

First distinguish a standard chart from a bespoke inline calculator or explainer using the handoff below. For standard quantitative chart tasks listed in this skill's chart-family index, `visualize-data` takes precedence over general visualization guidance and ad hoc HTML/CSS/JavaScript chart implementations. Use the actual Data chart component, not merely its analytical or design guidance.

Read the selected family guide, construct the standard chart configuration, and render it through the documented component for the destination. AppBlock and GenUI may host the Data fragment; they do not replace its renderer. Do not recreate supported chart marks with HTML tables, CSS, SVG, Canvas, or another library for convenience or assumed reliability.

This applies to synthetic examples and custom visual designs. Use the [documented fallback](docs/rendering/native-inline-visualizations.md#fallbacks) only for a confirmed unsupported requirement, unavailable delivery surface, or actual rendering failure after a targeted correction. Preserve explicit user-requested output formats.

## Inline calculators and explainers

A bespoke inline widget lets the reader change assumptions in a model and inspect recalculated outcomes, or interact with an explanation. Examples include a queue-staffing calculator or a capacity-planning tool. Route the whole widget to the installed `visualize:visualize` skill, including when it contains a standard line or bar chart. A chart that filters dates/categories, selects series or inspects existing observations remains a Data chart. A requested full dashboard or report retains its Data construction and selected destination; controls alone do not make it an inline widget.

Read the actual available Visualize skill and its applicable composition, controls and coordinated-state guides before authoring. Let that workflow own presentation, shared controls, typography, responsive layout, themes, accessibility, rendering, validation and inline delivery. Use its existing components; do not build a Data-owned widget framework or combine competing Data and Visualize composition rules. Data still owns the analytical method, verified calculations, units, assumptions and necessary provenance. Pass those reviewed inputs into the widget without changing the model to fit the presentation. Label modeled quantities as modeled, including fractional volume, so readers do not mistake them for observed counts.

Follow Visualize's validation workflow on the final fragment and fix reported errors. If a required helper is unavailable, use an available temporary preview with the actual pinned runtime to verify that the visual renders and requested controls update it and its readouts, including reset where present. Model-only checks, source inspection and stubbed rendering do not replace this check. If rendering or interaction cannot be checked, state that limitation; do not present the widget as verified.

Deliver the native inline content reference in the final response. A testing browser is temporary QA: never mark its tab as a deliverable or retain a second sidebar copy unless the user explicitly requested that output. Close or release only task-created QA tabs and stop only task-owned preview processes when finished; preserve unrelated user tabs. If cleanup is unavailable, state that limitation. Honor an explicit request for another delivery surface. This rule does not change sidebar delivery for standalone HTML reports/dashboards or Pages.

If Visualize or native inline delivery is unavailable, say which capability is missing and use an available fallback that preserves the answer and requested surface. Never claim that Visualize ran, or that a browser wrapper proves native inline placement. Do not install a replacement or silently turn the widget into a full dashboard.

## Chart selection

Read this skill, the [shared chart fields](docs/charts/shared.md), and the chosen family guide together. The family guide supplies the fields, limits and an example. Choose the relationship first, then render the same reviewed configuration on the target surface.

### Choose the chart

<!-- chart-family-index:start -->
- [`line`](docs/charts/line.md)
- [`area`, `stackedArea`](docs/charts/area.md)
- [`bar`, `horizontalBar`, `stackedBar`, `stackedBar100`, `horizontalStackedBar`, `horizontalStackedBar100`](docs/charts/bar.md)
- [`histogram`](docs/charts/histogram.md)
- [`scatter`](docs/charts/scatter.md)
- [`heatmap`](docs/charts/heatmap.md)
- [`pie`](docs/charts/pie.md)
- [`leaderboard`, `rankedList`](docs/charts/ranking.md)
- [`sparkline`](docs/charts/sparkline.md)
- [`funnel`](docs/charts/funnel.md)
- [`waterfall`](docs/charts/waterfall.md)
- [`boxPlot`](docs/charts/box-plot.md)
- [`sankey`](docs/charts/sankey.md)
<!-- chart-family-index:end -->

### Recommended chart scenarios

Use these chart families by default for the scenarios below. Honor explicit table-only, text-only, and no-chart requests.

- **Cohort retention:** use a heatmap by cohort and elapsed period to compare retention at matched tenure. Keep missing observations distinct from zero.
- **Estimates and uncertainty:** use the [uncertainty fields](docs/charts/shared.md) to show the estimate and its confidence bounds together.
- **Break down a change:** waterfall when contributions reconcile the opening and closing totals.
- **Compare groups:** use `bar` with a series for platform; preserve distinct plan codes such as “Edu” and “Education.” A donut is `pie` with an inner radius.
- **Ordered stages:** funnel for conversion across comparable populations; point to the transition that changed.

Keep reviewed numbers, observed zeroes, null gaps, units, and denominators intact. State decisive values, exceptions, uncertainty or scenario assumptions beside the chart. For contribution comparisons, name the leading amount and its share and compare it with the remainder. Use [data writing](../../shared/data-writing.md) when interpreting substantive findings. A table and chart may accompany one another when they answer different questions.

For bar chart height, row spacing, and painted thickness, use the [size controls and their limits](docs/react/bar-presentations.md#size-controls).

### Sources

Choose Sources independently of charts. Use [the inline Sources component](docs/rendering/inline-sources-receipt.md) when requested or when provenance, scope or transformations merit inspection, including beside a Markdown table. Simple supplied figures can be attributed directly. For scenarios use [controls](docs/charts/controls.md); for coordinated charts use [composition](docs/charts/composition.md) or [coordinated views](docs/charts/coordinated.md). Use [custom visuals](docs/rendering/custom-visuals.md) for an unsupported encoding.

## Chart rendering

Use the requested destination and its available renderer. An open Page, a browser tab, or a writable directory does not by itself change the destination. The [public configuration](docs/charts/public-api.md) is the same across the four routes.

### Page: use the standard chart component

Follow the [Page chart path](docs/rendering/page-chart-fragment.md): prepare reviewed JSON with the standard renderer, then use the unchanged HTML in the report and its source Page. Read the target Page and guidance before `create_page_visualization`; this operation uploads and inserts the chart once. Inspect its edit results and check the final saved references. Assume standard components render and deliver without browser validation. Custom charts and concrete failures use the separate checks in that guide.

### Work inline: render reviewed JSON

Where Work accepts visualization file references and an executor is available, save the selected family's reviewed chart configuration as JSON and run the installed Data renderer:

```sh
node "<data-plugin>/assets/visualize-data/scripts/runtime/render-chart.mjs" \
  --input /absolute/chart.json --output /absolute/chart.html --surface inline
```

The renderer validates the configuration, adds the pinned import and host styles, and returns a `reference`. Put that reference unescaped beside the finding in the final answer. Use a durable task-owned output path the host can read, on the executor that created it. The output is an inline fragment; keep standalone preview shells out of Work and Page embeds. For a different advertised native delivery capability, use that capability; never hand a cloud reader an inaccessible local path.

#### Author a chart fragment

```yaml
chart_base_url: "https://persistent.oaistatic.com/plugins/visualize/charts/data-analytics-plugin/1.2.1/charts"
```

Without an executor, author this literal standard-component fragment. Keep the published import, change the chart fields and reviewed rows, and prepend the installed `assets/visualize-data/assets/chart-host.css` inside a style element when the host does not supply it. Keep space reserved as the chart loads. Give the root a unique ID and select it by ID; the host can move scripts outside the root. The runtime supplies the interactive chart, legend, tooltips and error state.

```html
<section id="monthly-usage" data-data-chart data-viz-composition>
  <div data-viz-container style="min-height:380px"></div>
</section>
<script type="module">
  const { mountChart } = await import("https://persistent.oaistatic.com/plugins/visualize/charts/data-analytics-plugin/1.2.1/charts/element.js");
  const root = document.getElementById("monthly-usage");
  const container = root.querySelector("[data-viz-container]");
  const config = {
    id: "monthly-usage", title: "Monthly usage (GB)", height: 280,
    spec: { type: "line", x: "month", y: "usage", yLabel: "GB" },
    rows: [{ month: "Jan", usage: 12 }, { month: "Feb", usage: 18 }]
  };
  const chart = mountChart(container, config);
</script>
```

### Send the fragment in Chat

When the conversation advertises GenUI HTML, use this complete block with the same chart input. If it advertises DIL `<AppBlock>` instead, supply the fragment as raw HTML children. Keep the explanation outside the component. If neither is available, use the supported [native fallback](docs/rendering/native-inline-visualizations.md#fallbacks); distinguish a substitute chart or image from the interactive Data component.

```text
genui{"app_block":{"content":"<section id=\"monthly-usage\" data-data-chart data-viz-composition>\n  <div data-viz-container style=\"min-height:380px\"></div>\n</section>\n<script type=\"module\">\n  const { mountChart } = await import(\"https://persistent.oaistatic.com/plugins/visualize/charts/data-analytics-plugin/1.2.1/charts/element.js\");\n  const root = document.getElementById(\"monthly-usage\");\n  const container = root.querySelector(\"[data-viz-container]\");\n  const config = {\n    id: \"monthly-usage\", title: \"Monthly usage (GB)\", height: 280,\n    spec: { type: \"line\", x: \"month\", y: \"usage\", yLabel: \"GB\" },\n    rows: [{ month: \"Jan\", usage: 12 }, { month: \"Feb\", usage: 18 }]\n  };\n  const chart = mountChart(container, config);\n</script>"}}
```

### React reports and dashboards

Use the [dashboard](../build-dashboard/SKILL.md) or [HTML report](../../output_formats/html/report.md) starter's public `EvidenceChart` with the scoped reviewed rows. The current renderer runs behind the production chart interfaces. Example from `src/content/report/` or `src/content/dashboard/`:

```jsx
import React from "react";
import { EvidenceChart, useDataApp } from "../../data-app-public.jsx";

export function PlanActivity() {
  const { reviewedRows } = useDataApp();
  const rows = reviewedRows("active_users_by_plan", ["week"]);
  return <EvidenceChart id="activity" queryId="active_users_by_plan" title="Active users by plan"
    spec={{ type: "stackedArea", x: "week", y: "Pro", fields: ["Pro", "Team"], yLabel: "Active users" }}
    rows={rows} sourceRows={rows} />;
}
```

Use the [public chart bindings](docs/react/app-charts.md) for HTML apps; plain chart fragments use `mountChart`. For PNG or standalone chart HTML use the [export path](docs/rendering/native-inline-visualizations.md#standalone-preview-and-export).

### Verify an authored fragment

For literal or modified fragments, run `assets/visualize-data/scripts/runtime/check-chart.mjs chart.html` when an executor is available (`--surface page` for Pages). This checks source, not pixels. A `dynamic-payload` warning means the config was not validated: pass concrete initial and changed configurations as JSON files to the same checker. For example, numeric formatting requires `valueFormat: {style: "decimal", maximumFractionDigits: 2}`.

Inspect actual plotted marks or an explicit empty/error state and exercise an authored control; the outer element or a changing readout alone does not prove the chart rendered. Keep failures distinct from unavailable checks. Unchanged standard Page renderer output follows the Page path above.

Page fragments allow 256 KiB UTF-8, inline/HTML 1 MB subject to tighter host limits; 2,000 rows per chart and 2 MB JSON. Disclose necessary reductions. Keep previously published URLs in saved artifacts.
