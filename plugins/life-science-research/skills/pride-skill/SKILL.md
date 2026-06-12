---
name: pride-skill
description: "向 PRIDE Archive API 提交简洁请求，用于蛋白质组学项目发现和项目级元数据。适用于需要简明 PRIDE 摘要的场景。"
---

## Operating rules
- Use `scripts/rest_request.py` for all PRIDE Archive calls.
- Use `base_url=https://www.ebi.ac.uk/pride/ws/archive/v2`.
- Start with `projects` for discovery and keep page sizes modest.
- Prefer project-level metadata lookups over broad archive dumps.
- Re-run requests in long conversations instead of relying on older tool output.

## Execution behavior
- Return concise markdown summaries from the script JSON by default.
- Return raw JSON only if the user explicitly asks for machine-readable output.
- Prefer these paths: `projects` and `projects/<PXD accession>`.

## Input
- Read one JSON object from stdin.
- Required fields: `base_url`, `path`
- Optional fields: `method`, `params`, `headers`, `json_body`, `form_body`, `record_path`, `response_format`, `max_items`, `max_depth`, `timeout_sec`, `save_raw`, `raw_output_path`
- Common PRIDE patterns:
  - `{"base_url":"https://www.ebi.ac.uk/pride/ws/archive/v2","path":"projects","params":{"keyword":"proteomics","pageSize":10},"max_items":10}`
  - `{"base_url":"https://www.ebi.ac.uk/pride/ws/archive/v2","path":"projects/PXD001357"}`

## Output
- Success returns `ok`, `source`, `path`, `method`, `status_code`, `warnings`, and either compact `records` or a compact `summary`.
- Use `raw_output_path` when `save_raw=true`.
- Failure returns `ok=false` with `error.code` and `error.message`.

## Execution
```bash
echo '{"base_url":"https://www.ebi.ac.uk/pride/ws/archive/v2","path":"projects","params":{"keyword":"proteomics","pageSize":10},"max_items":10}' | python scripts/rest_request.py
```

## References
- No additional runtime references are required; keep the import package limited to this file and `scripts/rest_request.py`.
