---
name: index
description: "Answer product and business questions with data and route data-related work to the right focused workflow. Use for requests involving data, metrics, trends, comparisons, drivers, KPIs, analysis, dashboards, reports, charts, tables, SQL, notebooks, spreadsheets, market sizing, data quality, reusable data context, data definitions, or working preferences, whether or not Data is at-mentioned. Dashboards can use uploaded spreadsheets, CSVs, or TSVs as source data without making the deliverable a spreadsheet. Do not use Data for general writing, editing, coding, or explanations that require none of these workflows."
---

# Data and shared instructions

For concrete work, use the focused skill that matches the request. Skills can be invoked directly; they do not need to come through this index.

Before choosing prose or a table, apply [presentation routing](#output-and-presentation): meaningful quantitative patterns warrant a chart, and consequential evidence processing can warrant Sources independently. Use [visualize-data](../visualize-data/SKILL.md) for those components, including implicit requests.

For dashboards, [build-dashboard](../build-dashboard/SKILL.md) governs construction and validation. For supported quantitative charts, [visualize-data](../visualize-data/SKILL.md) governs chart implementation. Before selecting a chart renderer, use its [inline widget handoff](../visualize-data/SKILL.md#inline-calculators-and-explainers) for a bespoke calculator, parameter-driven planning tool or interactive explainer. General website and host-container workflows must preserve Data chart and dashboard components, including when a follow-up changes the delivery destination.

From this index, select the focused skills below and read their `SKILL.md` files together with the currently applicable shared guides directly in one parallel batch. Follow the links without walking through intermediate guides to rediscover that same reading set. Defer references whose triggers do not yet apply.

**Read each required file or section once per task.** Reuse complete instructions already in context across skill handoffs; another link or “read before use” instruction does not require another read. Recover only missing or truncated text, or changed instructions, without repeating complete files.

For instruction reads, set a generous output budget on **both the file-read command and its enclosing tool call**. With `functions.exec`, start the batch with `// @exec: {"max_output_tokens": 64000}` and set each `tools.exec_command` read to `max_output_tokens: 20000`; increase these or split into disjoint batches if needed. Budget at least 1.5× the combined size of the selected files, including focused skills and external guides. A large per-command limit alone does not prevent the enclosing batch from truncating its output. Return each path and the raw `result.output`, rather than serializing the full tool-result envelope. Read required files in full on the first pass; request an anchored section only when that is the applicable guidance.

## Short paths

- **“What can Data do?” or examples only:** answer here, then stop. Data can explain a metric change, design KPIs, compare retention, size an opportunity, or build a source-backed report or dashboard. Give relevant examples without starting one or checking connectors. Ordinary writing, formatting or code repair needs no Data workflow.
- **Get started, choose a first task, or tour a named homepage example:** use [onboarding](../onboarding/SKILL.md) and its short welcome or tour path. Resume a concrete request interrupted by installation without requiring setup.
- **Existing definitions or business framing only:** use the metric definitions reference below, then return a focused, cited answer. A lookup alone needs neither visualize-data nor a Sources widget. Persist a definition or domain change only when explicitly requested, through its authorized maintenance workflow.

## Direct paths for supplied evidence

When the question and evidence are supplied, skip source discovery unless something material is missing. Read the applicable files below together; these paths supersede the general reading bundle.

### Reports

- **Report core:** [Build Report](../build-report/SKILL.md), [shared Data rules](../../shared/shared-skill-instructions.md), [analysis quality](../../shared/analysis-quality.md) and [data writing](../../shared/data-writing.md). Reuse files already read. For format conflicts, conversions or recovery add [output selection and handoff](../../shared/output-and-template-handling.md).
- **Question:** For an investigation add [investigative reports](../build-report/docs/investigative-report.md); for a metric change add [metric diagnostics](../metric-diagnostics/SKILL.md). For authored source summaries add [report Sources](../build-report/docs/report-sources.md).
- **Destination:** For HTML/Sites add the [HTML report starter](../../output_formats/html/report.md). For a native Page add the [Page report starter](../../output_formats/space_page/report.md). For other formats use the selected format’s authoring path. The generated HTML project supplies its editable files, components and build instructions.

### Dashboards

- **Local dashboard:** read [Build Dashboard](../build-dashboard/SKILL.md) for its starter, views and checked handoff. Read the copied authoring note and React/data files together after preparing the app. Use additional source/metric/template guides for missing evidence, undefined metrics or an explicit template.

### Plots

- **Inline calculator or explainer:** use the [Visualize handoff](../visualize-data/SKILL.md#inline-calculators-and-explainers) before loading Data chart-family or dashboard guides. Data retains the analytical method, verified calculations and necessary provenance.
- **Chart:** read [visualize-data](../visualize-data/SKILL.md), [shared types](../visualize-data/docs/charts/shared.md) and the [selected family](../visualize-data/SKILL.md#choose-the-chart) together when known. Include only the applicable delivery guide: [native inline](../visualize-data/docs/rendering/native-inline-visualizations.md), [Page embed](../visualize-data/docs/rendering/page-chart-fragment.md) or [React in HTML](../visualize-data/docs/react/app-charts.md). For Sources without a chart, use [inline Sources](../visualize-data/docs/rendering/inline-sources-receipt.md) when delivering in chat.

### Processing and exports

Use the smallest applicable tool or analytical skill and deliver a usable file link. When the result is a new standalone HTML report or dashboard, complete [native opening](../../shared/output-and-template-handling.md#opening-and-report-handoff) before the final response when available. Additional analytical questions still follow the chart/Sources decision below; an export alone needs neither component.

## Focused skills

Choose the analytical skill by the question and the delivery skill by the output; a report, chart or export does not replace the analysis. For example, explaining declining retention in an HTML report uses metric-diagnostics + build-report; a weekly KPI workbook uses kpi-reporting + the spreadsheet authoring skill. Load the smallest applicable set. Converting an existing artifact does not restart analysis: use its conversion workflow to preserve content and state. A new document or deck can use its native authoring path.

For a request to continue, recalculate, or revise an existing analysis, resume the applicable analytical and delivery skills and perform the requested work. Preserve the existing artifact and output choice. Use answers-follow-up only for optional next-task suggestions; a selected suggestion is a concrete request to execute through the relevant workflow.

| Skill | Use for | Approx. tokens |
|---|---|---:|
| [product-business-analysis](../product-business-analysis/SKILL.md) | Business decisions, product or experiment analysis | 3.5k |
| [metric-diagnostics](../metric-diagnostics/SKILL.md) | Explain a metric change or its drivers | 3.5k |
| [kpi-reporting](../kpi-reporting/SKILL.md) | KPI summaries, recurring business reviews | 4k |
| [design-kpis](../design-kpis/SKILL.md) | Define success metrics and guardrails | 3k |
| [market-sizing](../market-sizing/SKILL.md) | Size markets or opportunities | 2.5k |
| [analyze-data-quality](../analyze-data-quality/SKILL.md) | Profile data and diagnose quality problems | 3.5k |
| [validate-data](../validate-data/SKILL.md) | Audit calculations, claims or an existing analysis | 3k |
| [answers-follow-up](../answers-follow-up/SKILL.md) | Offer optional next-task suggestions | 1k |
| [build-report](../build-report/SKILL.md) | Narrative reports and documents | 6.5k |
| [build-dashboard](../build-dashboard/SKILL.md) | Monitoring or exploratory dashboards | 1.5k |
| [visualize-data](../visualize-data/SKILL.md) | Charts, inline composition and warranted Sources inspectors | 2.5k |
| [jupyter-notebooks](../jupyter-notebooks/SKILL.md) | Requested notebooks or computational artifacts | 4k |
| [convert-to-doc](../convert-to-doc/SKILL.md) | Convert an existing Data app to a document | 2k |
| [convert-to-slides](../convert-to-slides/SKILL.md) | Convert an existing Data app to slides | 2k |
| [report-to-pdf](../report-to-pdf/SKILL.md) | Export a report to PDF | 1.5k |
| [share-artifact-summary](../share-artifact-summary/SKILL.md) | Requested sharing of an existing artifact | 2k |
| [publish-artifact-to-sites](../publish-artifact-to-sites/SKILL.md) | Publish or update an artifact on Sites | 5k |
| [schedule-refresh-jobs](../schedule-refresh-jobs/SKILL.md) | Requested recurring artifact refresh | 2k |
| [onboarding](../onboarding/SKILL.md) | Get started or tour a homepage example | 4.5k |
| [customize-data-plugin](../customize-data-plugin/SKILL.md) | Maintain reusable Data context or definitions | 4.5k |

Data’s `visualize-data` owns standard quantitative charts, including ordinary filtering and selection. Bespoke inline calculators and explainers use the Visualize handoff even when their main visual is a supported chart. General conceptual explanations and UI previews do not become Data tasks merely because they are visual. `visualize-data` composes charts and Sources in chat; reports and dashboards own their embedded components.

## Output and presentation

When composing substantive analytical text, read [data writing](../../shared/data-writing.md) with the selected skill once and reuse it across surfaces. Brief answers and file handoffs need no extra read; prose alone does not require visualize-data.

Choose the presentation alongside the analytical workflow, before a source helper or calculation can choose it for you. Apply explicit format requests, user-selected templates and existing artifact revisions first under [output formats and templates](../../shared/output-and-template-handling.md#output-format-selection). The source format is not the output format; an uploaded workbook can supply an inline answer, report or dashboard.

When missing source evidence blocks the requested findings, request it inline before creating an artifact. Create a placeholder or outline only when specifically requested.

| Request and scope | Presentation and instructions to load |
| --- | --- |
| Explicit inline-only or chat-only | Keep the answer in the final message; use the widget handoff below for calculators, or [visualize-data](../visualize-data/SKILL.md) for standard charts and warranted Sources. |
| Requested table | Put the table in the final message. Choose warranted Sources independently; a table request alone does not prohibit inspection. |
| Explicit text-only or no embeds | Honor the constraint; keep necessary source and method details in text. |
| A requested report, document or other narrative artifact | Use [build-report](../build-report/SKILL.md) and the selected format's authoring path. |
| A requested dashboard for monitoring or exploration | Use [Build Dashboard](../build-dashboard/SKILL.md); add specialist guidance for unresolved evidence or analytical design. |
| A bespoke inline calculator, parameter-driven planning tool or interactive explainer | Use the [Visualize handoff](../visualize-data/SKILL.md#inline-calculators-and-explainers); do not start a full dashboard for this request. |
| No explicit format, and three or more distinct analytical questions need answers | Deliver an inline summary plus a report: use the inline chart/Sources guidance below and [build-report](../build-report/SKILL.md). |
| Inline chart or functional Sources inspector | Read [visualize-data](../visualize-data/SKILL.md); chart types are unnecessary for Sources-only delivery. |
| Other questions and analyses | Answer inline, applying the chart/Sources guidance below. |

Count independent questions requiring distinct findings, not metrics, source files, calculation steps, headings or chart series within one question. Comparing two plans across several measures can remain one question. Reviewing adoption, diagnosing reliability and deciding pricing are three. Apply the same rule if the requested scope expands during the task; do not manufacture extra questions to cross the threshold. An explicit output choice continues to take precedence. A dashboard is created when requested, not inferred from a large number of questions.

For the combined path, give the useful answer and key qualifications in chat and link the completed report containing detailed evidence and charts. Preserve both endpoints, units and scenario qualifiers in a before/after finding. Keep charts and source inspection in the report unless needed separately in chat. A requested sharing draft should contain the existing report link; drafting does not authorize sending or rebuilding it. A delivered Page follows the [Page handoff](../../shared/output-and-template-handling.md#opening-and-report-handoff). Reuse reviewed calculations across surfaces. Complete a selected report rather than merely offering it; do not routinely offer an additional report after smaller analyses.

Reports default to a private personal Spaces Page through an authorized creation route, independent of Page skills. [Output formats and templates](../../shared/output-and-template-handling.md#output-format-selection) owns creation-tool discovery before an HTML fallback, destination details and recovery. This release has no saved Data settings. Explicit templates and formats still take precedence. New HTML reports start with the [HTML report guide](../../output_formats/html/report.md). Page reports use the [Page report starter](../../output_formats/space_page/report.md).

For an analytical question, show the quantitative relationship that answers it: trends around an event, comparisons or concentrated gaps, distributions, targets, uncertainty and associations. Use [visualize-data](../visualize-data/SKILL.md) even when the user did not name a chart. A short answer or small dataset can still need one. Tables serve exact lookup and calculations; they do not replace a useful view of the pattern. Honor explicit no-chart constraints. Isolated values and pure exports need no chart.

Choose a Sources inspector independently when requested or when meaningful query scope/filters, joins/exclusions, reconciliation, weighting or consequential assumptions determine the result. Explaining the formula in prose does not replace this inspection. Data outside the prompt alone, transparent supplied values, straightforward sums/ratios and ordinary citations need none. Use [visualize-data](../visualize-data/SKILL.md#sources) for warranted Sources, including alongside a table. Pure exports and report-link handoffs need no inspector.

For actions on an existing artifact, use [share-artifact-summary](../share-artifact-summary/SKILL.md) for requested sharing, [output conversion](../../shared/output-and-template-handling.md#exports-and-output-type-conversion) for exports, and [schedule-refresh-jobs](../schedule-refresh-jobs/SKILL.md) for a recurring refresh. Preserve the artifact's identity and selected destination. A generic share request does not identify a recipient or grant publication rights.

## UI component reference

Read only the atomic references needed for the selected surface. These guides live under `output_formats/html/docs/components/`, with the same categories as reusable source under `output_formats/html/src/ui/`. Sources and narrative also cover app-specific evidence and report bindings. They are references, not separately invoked skills.

Native inline visuals and Pages use the chart element plus host controls. React filters, cards, tables, and layout currently ship with the embedded app runtime and its providers; no standalone React controls entry is available. For app imports, source-mode lookup, and the boundary between shared components and authored React, follow the [Data app contract](../../output_formats/html/docs/app-components.md#resolve-the-component-reference).

| Category and use | Public components or contract | Atomic references |
| --- | --- | --- |
| Charts | Standard families, controls, composition and app bindings | [visualize-data](../visualize-data/SKILL.md) |
| Controls: filters, dates and scenarios | `Filters`, `InlineFilters`, `Dropdown`, `DateRangePicker`, `Switch`, `SegmentedControl`, `Slider`, `RangeSlider`, `NativeSelect`, `useSectionFilters`, `useDashboardTabs` | [Controls](../../output_formats/html/docs/components/controls/controls.md), [filtering and exploration](../../output_formats/html/docs/components/controls/filtering.md) |
| Tables: reviewed records and search | `DataTable` (`Table` alias), built-in search, sorting and pagination | [Tables](../../output_formats/html/docs/components/tables/tables.md) |
| Metrics: values, trends and comparisons | `MetricCard`, `MetricCardTabs`, `MetricSparkline` and comparison formatters | [Metric cards](../../output_formats/html/docs/components/metrics/metric-card.md), [comparison formatting](../../output_formats/html/docs/components/metrics/comparison-formatting.md) |
| Layout: composition and navigation | `DataComponent`, `Section`, `SectionHeader`, `SectionNavigator`, `SortableRegion`, `SortableItem` | [Cards and layout](../../output_formats/html/docs/components/layout/layout.md), [sortable layout](../../output_formats/html/docs/components/layout/sortable-layout.md) |
| Primitives: local panels, actions and overlays | `Tabs`, `TabPanel`, `Button`, `Dialog`, `ContainedDialog`, `Menu`, menu items/groups, `InfoTooltip`, `Tooltip`, `TruncatedText`, `Icon` | [Shared primitives](../../output_formats/html/docs/components/primitives/primitives.md) |
| Sources: evidence and loading | `QueryDataBoundary`, `SourceInspector`, `SourceSidebar` and source metadata | [Sources](../../output_formats/html/docs/components/sources/sources.md), [async data](../../output_formats/html/docs/components/sources/async-data.md) |
| Narrative: app report bindings | `ReportSection`, `EditableText`, `RichNarrative`, `ExecutiveSummary` | [Reports](../../output_formats/html/docs/components/narrative/reports.md) |

## What the reader sees

The shared writing guide owns cross-surface wording and numerical presentation. Follow the focused build skill for layout and delivery. Source receipts describe provenance, not answer confidence; never reinterpret provider, retrieval or classification scores as support for an analytical claim.

Keep SQL in inspectable evidence unless requested or needed for interpretation, including when context skills prefer showing SQL. Use descriptive [source links](../../shared/shared-skill-instructions.md#links-in-the-conversation), or a plain source label when no useful link exists. Never expose credentials, hidden reasoning, direct personal contact or payment identifiers, or unverified calculations.

## Shared instructions: table of contents

Use the direct paths above for supplied reports, dashboards and charts, and the short paths for capability help or onboarding. On the general path, **Critical** precedes substantive work; **Important** and **As needed** apply when the row’s condition is met. Batch known needs and read only missing guidance. Sizes are approximate. For Page charts, pair visualize-data with the [Page report starter](../../output_formats/space_page/report.md); for a warranted Sources inspector, use [Sources delivery](../visualize-data/docs/rendering/inline-sources-receipt.md).

| Priority | Shared reference | Approx. tokens | When it applies |
|---|---|---:|---|
| Critical | [Shared Data instructions](../../shared/shared-skill-instructions.md) | 2k | Start concrete work: common rules, task preferences, accessible presentation and links. |
| Important | [Source selection and dependency resolution](../../shared/source-selection.md) | 2k | Establish source restrictions and authority before a helper or query; check availability and use bounded discovery. |
| Important | [Metric definitions and business context](../../shared/metric-definitions.md) | 1.5k | Resolve company-specific meaning before accepting a controlling source, choosing tables or interpreting measurements. |
| Important | [Task intake](../../shared/task-intake.md) | 1.5k | Proceed with an assumption, ask asynchronously, or handle one of the narrow blocking cases. |
| Important | [Templates and prior work](../../shared/templates-and-prior-work.md) | 1k | Find relevant templates or prior work for a substantial analysis, report or dashboard. |
| Important | [Analysis quality](../../shared/analysis-quality.md) | 3k | Check analytical claims, comparability, denominators and conclusions as evidence changes. |
| Important | [Data writing](../../shared/data-writing.md) | 1k | Compose substantive analytical text across surfaces; skip brief answers and handoffs; reuse once loaded. |
| Important | [Dashboard quality](../../shared/dashboard-quality.md) | 2k | Check a dashboard’s hierarchy, behavior and rendered result. |
| Important | [Output formats and templates](../../shared/output-and-template-handling.md) | 3k | Create, revise, convert or recover a durable artifact in the selected destination. |
| As needed | [HTML app reference](../../output_formats/html/README.md) | 0.5k | For questions the starter or generated project does not answer, read only the relevant topic: [reviewed data](../../output_formats/html/docs/evidence.md#reviewed-data-and-provenance), [refresh](../../output_formats/html/docs/refresh.md#local-and-hosted-data-lifecycle) or [delivery](../../output_formats/html/docs/delivery.md#publication-and-final-delivery). |
| As needed | [Source setup and access recovery](../../shared/source-setup.md) | 4k | A concrete access gap, useful integration, pending connection, or no usable source. |
| As needed | [Table usage metadata](../../shared/table-usage.md) | 1.5k | Include available usage evidence for a warehouse table in a Data app or inline Sources receipt. |
| As needed | [Template previews](../../shared/template-previews.md) | 2.5k | Prepare a requested template picker, including local rendering fallbacks; missing previews need not delay it. |
| As needed | [Automation offers](../../shared/automation-offers.md) | 0.5k | Offer to repeat an eligible completed analysis; report or dashboard refresh has its own rule. |
