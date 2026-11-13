# Native inline delivery

Use this reference after an inline chart has been selected. It does not replace a selected report, Page, dashboard, notebook, image or other explicit output. Keep Data's chart choice, reviewed values and interpretation independent of the host's delivery mechanism.

MCP servers and other callable tools can still supply reviewed source data; they do not determine the renderer. Embed only bounded fields needed for the displayed marks or requested interaction; omit hidden reasoning, credentials, secrets, tokens, direct personal contact/payment identifiers, and other unnecessary sensitive values. Keep material caveats beside the chart and follow the shared [data writing guide](../../../../shared/data-writing.md).

## Data charts inside GenUI

For straightforward quantitative charts in Chat, use the [Data chart component](../../SKILL.md), including ordinary chart filters and selection. Bespoke inline calculators and explainers use the [Visualize handoff](../../SKILL.md#inline-calculators-and-explainers) instead. When the host provides an HTML container, deliver the same Data chart fragment through it. The component owns marks, axes, legend, theme, tooltips and readiness; GenUI owns the enclosing surface. This path is Data fragment → host HTML container → browser execution → Data CDN runtime. It does not invoke the separate Visualize plugin, its checker or its standalone wrapper.

Use the active host's invocation syntax:

- DIL `<AppBlock>`: put the fragment directly inside the component as raw HTML/JavaScript children, following the host's documented attributes and constraints. Do not JSON-escape the fragment or put it in a Markdown code fence.
- GenUI `app_block`: use the [complete GenUI example](../../SKILL.md#send-the-fragment-in-chat). Its `content` is the same HTML fragment, JSON-escaped.

Emit the live component or reference in the final answer. Preserve the authored fragment, pinned import and `mountChart` call during final-answer assembly; do not redraw a second version using native `<svg>` or `<Chart>`. Never print bare HTML/JSON or put an executor-local file path in an app block. Do not invent a surface when the host does not provide it.

- Keep the selected Data chart family and pinned module import from the main guide when the active host permits it. Inability to deliver a Work file reference is not evidence that Data's component cannot run.
- Define the chart config directly in the module that calls `mountChart`, as in the main guide. AppBlock streaming may move JSON script elements out of their authored section. A `null.textContent` config-lookup error calls for this targeted correction before changing chart family or renderer; it does not establish an import failure. Keep RPC timeouts separate from config-loading errors.
- Embed bounded reviewed rows. Do not fetch data, add API calls or change network permissions. Honor any stricter active host contract.
- Keep the fragment free of document wrappers and prose. Put interpretation and material caveats beside it in the answer. Use unique IDs, labeled controls and the shared component's lifecycle; add no loading text, timers or visibility gates.
- When an executor exists, generate the standard fragment from reviewed JSON with the main guide's `render-chart.mjs --surface inline` route, then put its contents into the native reference. Without one, author against the same documented types and do not claim local checks ran.
- Check the actual rendered result when testing: correct marks and values, an authored interaction, and a reload. A saved file or emitted reference alone does not prove rendering. Record host failures separately from a confirmed component/import error.

Where the host visualization-reference capability is the active contract, use the main guide's file reference instead. This is commonly available in Codex tasks and Work; native HTML/AppBlock is commonly available in Chat. Choose based on the current conversation's capabilities, not whether it is viewed in a browser or desktop app. Pages use their supported visualization operation. Do not invent an AppBlock, Page tool or executor-local path when that capability is absent.

## Standalone preview and export

For a standalone standard Data chart, use the same reviewed JSON with the
installed renderer's HTML surface:

```sh
node "<data-plugin>/assets/visualize-data/scripts/runtime/render-chart.mjs" \
  --input /absolute/chart.json --output /absolute/chart-export.html --surface html
```

Use the standalone wrapper below for a concrete preview or a custom-control
fragment. Native inline and Page delivery do not run or require `render.py`;
retain the unwrapped fragment for those surfaces. For a new report/dashboard,
use its selected Data workflow instead.

A browser opened only for inline QA is temporary. Do not call `markDeliverable()` or retain it as a second sidebar output. After inspection, close or release only task-created QA tabs and stop only task-owned preview processes; preserve unrelated tabs and report unavailable cleanup. Deliver the native inline reference in the final answer. An explicitly requested separate output and sidebar opening of a standalone report/dashboard or Page retain their own delivery workflow.

Resolve the helper under the installed **Data** plugin, not another plugin with the same filename:

```sh
python3 "<data-plugin>/assets/visualize-data/scripts/runtime/render.py" /absolute/chart.html --serve
python3 "<data-plugin>/assets/visualize-data/scripts/runtime/render.py" /absolute/chart.html /absolute/chart-export.html
```

After editing the fragment, regenerate the same task-owned export with `--force`; without it, an existing file is deliberately preserved. Confirm the output is the export being revised, not a source file or another user's artifact. Pass `--title` for a useful document title rather than inheriting a working filename. In a desktop task, use its local browser capability to inspect a loopback preview; a browser connector on a different host cannot reach that local server. Elsewhere use the browser on the execution host. Do not probe unrelated browser tools after the preview is already reachable.

These commands build a restricted standalone HTML document; they do not run the chart checker. Use Data's `check-chart.mjs` for standard Data charts. Do not substitute `render.py --check` or the separate Visualize plugin's helper. Preserve the pinned Data import and component when wrapping a standard chart. Review any host-only interactions before standalone export.

For a requested scenario tool with custom controls, author only the fragment and let this helper supply both the exported document and its preview. Omit `--port` to use an available loopback port; read the actual URL from the running process and keep that process alive for preview. Do not probe a free port and release it before binding, guess a fixed port, or stop an unrelated server after a collision. Reuse this preview for custom-control checks and export the same fragment after the final edit. Page reports need this companion only when explicitly requested.

Choose numeric-control precision from the measure: integer steps for discrete counts, fractional steps for rates, durations, expected volumes and monetary amounts when meaningful. Keep blank, invalid and missing inputs distinct from zero; commit only finite values within the stated domain. Allow signed changes when the measure permits them without allowing negative populations or durations. Retain full precision in calculations and chart rows; normalize a displayed rounded zero to `0` rather than `-0`. Derive controls, readouts, tables and the complete standard chart config from one state object. For plain HTML, `mountChart(container, initialConfig)` returns the chart element; update it with `chart.config = nextConfig` (the complete config with new rows). It has no public `update()` or `setConfig()` method. See the [public API](../charts/public-api.md) only for additional lifecycle details. Reset restores every default and clears pending updates. Test a fractional input, a valid boundary, rapid input followed by reset, and a meaningful changed result; do not require a particular business model or a loss case when it is irrelevant.

The Data-bundled wrapper permits chart modules under `https://persistent.oaistatic.com/plugins/visualize/charts/`. An actual host may apply a different or stricter policy. A successful standalone check is evidence for that document only; inspect the real target surface for claims about its rendering, interactions or reload behavior. Do not change host permissions or CDN pins to work around an inconclusive preview.

## Defer broader Chat experiences to GenUI

Bespoke inline calculators and interactive explainers use the installed Visualize workflow through the [widget handoff](../../SKILL.md#inline-calculators-and-explainers). Other conceptual diagrams and custom interfaces follow their selected visual workflow and the active host contract. Do not force them into Data's chart API or treat every GenUI request as quantitative analysis. A normal chart with a filter remains a Data chart.

Pages and HTML reports/dashboards retain their existing Data components and selected delivery. An inline fallback must not silently change an HTML-default or Page-default report treatment.

## Fallbacks

Use a fallback only for a confirmed unsupported encoding, unavailable delivery
surface or actual rendering failure after one targeted correction. Preserve
the analytical relationship, reviewed rows, units and caveats. A resource-reading
problem, failed calculation or plotting command, or inconclusive preview does
not establish a Data component or delivery failure. Select from the host's
available delivery capabilities before replacing the chart with a table.

| Available capability | Fallback |
| --- | --- |
| Only inline delivery is unavailable; Data supports the encoding and the host can deliver viewable HTML with the chart runtime available | Read the selected Data family guide and render its reviewed JSON with `render-chart.mjs --surface html` as shown in [standalone export](#standalone-preview-and-export). Include the saved HTML link beside the finding in the final answer. This delivers the Data chart without claiming native inline rendering. |
| Host-native `charts_widget_v2` and a simple bar, line, pie or fixed-size scatter | Use its documented JSON chart contract. Do not approximate a waterfall, funnel, heatmap or bubble chart with an unrelated family. |
| Native HTML but the required encoding is unsupported by Data | Follow [custom visual guidance](custom-visuals.md) and the active host contract; record the specific limitation. |
| No suitable interactive or HTML-file delivery, or explicit scientific/static/image request | Create a reproducible static chart with standard plotting tools and inspect it when possible. |
| No visual can be produced or delivered through the available routes | Preserve the answer and exact values in Markdown or prose; do not claim a visual rendered. |

Only use a native widget when the active host supplies it. For `charts_widget_v2`, the current shape is `genui{"charts_widget_v2":{"content":{...}}}`; the documented chart spec belongs inside `content`, without another wrapper or stringification. Use any differing syntax supplied by the host. Mermaid is not a quantitative chart fallback.
