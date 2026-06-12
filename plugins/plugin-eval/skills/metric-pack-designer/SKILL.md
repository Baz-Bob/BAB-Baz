---
name: metric-pack-designer
description: "为 plugin-eval 设计自定义指标包，供团队添加本地评估标准，生成与 schema 兼容的检查项和指标。适用于用户想定义自己的评估维度或可视化方式的场景。"
---

# Metric Pack Designer

Use this skill when the user wants to extend `plugin-eval` with a local rubric.

## Workflow

1. Clarify the custom rubric categories and target kinds.
2. Define the smallest useful `checks[]` and `metrics[]` payload.
3. Create a metric-pack manifest plus a script that prints JSON to stdout.
4. Run the pack through `plugin-eval analyze <path> --metric-pack <manifest.json>`.

## Design Rules

- Keep IDs stable across runs so comparisons stay meaningful.
- Emit only `checks[]`, `metrics[]`, and optional `artifacts[]`.
- Do not try to overwrite the core score or summary.
- Prefer deterministic local signals over subjective text generation.

## Reference

- `../../references/metric-pack-manifest.md`
