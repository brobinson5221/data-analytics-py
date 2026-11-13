# A standard interactive chart in a Space Page

Use the standard chart component for Page charts. Write the reviewed configuration to JSON and prepare the fragment once:

```sh
"<codex-node>" "<data-plugin-root>/assets/visualize-data/scripts/runtime/render-chart.mjs" --input /absolute/chart.json --output /absolute/chart.html --surface page
```

It validates the configuration before writing, includes the pinned import and host styles, and enforces the Page size limit. A successful receipt has `validation: "payload-checked"` and `rendering: "not-checked"`. Use its output unchanged for the report and source Page; an additional offline check of that unchanged generated fragment is unnecessary. The JSON uses the shared chart fields and selected family. For example:

```json
{
  "id": "weekly-activity",
  "title": "Weekly active users",
  "spec": {
    "type": "line", "x": "week", "y": "users",
    "yLabel": "Active accounts", "showValues": true,
    "valueFormat": {"style": "decimal", "maximumFractionDigits": 0}
  },
  "rows": [{"week": "2026-09-06", "users": 1400}, {"week": "2026-09-13", "users": 1500}]
}
```

If specifying `valueFormat`, include its `style` (`decimal`, `percent`, or `currency`); currency also needs its currency code. Omit `valueFormat` entirely to use the chart's default formatting. Keep the data's units and scale: do not infer percent or currency from the values.

**Upload only after validation succeeds.** Wait for the command result before calling `create_page_visualization`; a returned tool result with a nonzero exit code is a failure, even if the surrounding orchestration continued. On failure, correct the input and rerun preparation. Do not upload the invalid fragment, an older file at the same path, or an unchecked replacement. This applies to both the report and its source Page.

Supply only reviewed plotted fields, retaining precision and explicit missing values. Keep queries, unplotted source fields and calculation detail in the source Page. The UTF-8 fragment must fit 256 KiB; make any reduction explicit. Pass the fragment itself to the active Page visualization tool and follow the [report/source workflow](../../../../output_formats/space_page/report.md#create-connect-and-finish). Reuse the same fragment in both places.

Assume the successfully prepared and saved standard component renders. Check the save results and final Page references, open the report for the user, and deliver without browser polling, screenshots, hover tests, theme checks or a second offline check. Do not describe assumed rendering as visually verified. Standard component rendering is tested during release qualification.

## Custom charts and fallbacks

Use [custom visuals](custom-visuals.md) only for an unsupported encoding or explicitly requested custom behavior. If no executor is available, use the same standard component through the [literal fragment](../../SKILL.md#author-a-chart-fragment). Authored or modified HTML requires `check-chart.mjs chart.html --surface page` when available, plus a bounded check of the custom behavior in the intended reader.

For an explicit visual-review request or a concrete reported failure, follow the shared [chart preservation procedure](../../../../shared/shared-skill-instructions.md#preserve-charts-during-verification). Prefer the host’s in-app viewer and assess each chart on each Page separately. Preserve an interactive chart that works in an intended reader. Loading, a timeout, unavailable inspection or a generic host notice alone does not justify adding an image; record the reader limitation without changing the chart.

If a confirmed rendering or delivery failure remains after those checks and any applicable scoped repair, and no intended reader is known to render that chart, a verified static fallback can replace it. Export and inspect an image from the same reviewed chart input, then replace the failed embed through supported, guarded Page edits. If the image has already been inserted, remove only the failed embed rather than adding another image. Keep the source link immediately below the remaining chart, and preserve unrelated content and working charts. Retain the original HTML and reference in task evidence and disclose that interaction is unavailable.

Keep one representation of each chart per Page; do not retain the failed embed under a collapsed heading. Honor an explicit request for both formats. Reusing the chart on a separate source Page is intentional: assess that Page independently and preserve its chart and source relationship. Check the final saved blocks, chart count and source links without restarting browser verification.
