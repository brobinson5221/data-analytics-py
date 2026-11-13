---
name: enhance-notebook-markdown
description: Review and polish user-written Markdown cells in this project's Jupyter notebooks when asked to enhance notebook explanations or write-ups, preserving the author's meaning and checking claims against saved code and outputs.
---

# Enhance notebook Markdown

Read the requested notebook directly from the workspace, including its Markdown, relevant code, and saved outputs. Use the notebook named by the user or current conversation. If several notebooks are equally plausible, ask which one.

Edit the requested Markdown cells in place. When the request is general, focus on the user's own explanations. Use conversation history to identify wording previously supplied by Codex and avoid rewriting it unnecessarily. Do not claim authorship distinctions that cannot be established.

Preserve the author's first-person voice, intent, conclusions, and level of technical understanding. Improve spelling, grammar, clarity, and flow using plain language. Add concise explanations only when supported by the existing analysis or agreed project scope. Keep existing attribution and useful formatting.

Check factual claims against the relevant saved code and outputs. Distinguish intended analysis from completed work. Do not invent results, claim checks passed without evidence, or turn an association into a causal conclusion. If a claim needs verification, qualify it and report the gap. Saved outputs can be stale, and unsaved kernel state is unavailable through the notebook file.

Change only Markdown source. Preserve code, outputs, execution counts, cell IDs, metadata, and cell order. Prefer targeted edits that avoid reformatting the entire notebook. Do not execute cells or download data solely to polish prose unless the user requests that work.

After editing, parse the notebook as JSON and confirm that only intended Markdown source changed. Briefly report which explanations were improved and any claims that remain unverified.
