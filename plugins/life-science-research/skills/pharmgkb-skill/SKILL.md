---
name: pharmgkb-skill
description: "向 PharmGKB API 提交简洁请求，查询基因、变异体、临床注释、用药指南和搜索。适用于需要简明 PharmGKB 摘要的场景。"
---

## Operating rules
- Use `scripts/rest_request.py` for all PharmGKB API calls.
- Use `base_url=https://api.pharmgkb.org/v1/data`.
- Single object lookups usually do not need `max_items`; list and search endpoints are better with `max_items=10`.
- Re-run requests in long conversations instead of relying on older tool output.
- Treat displayed `...` in tool previews as UI truncation, not literal request content.

## Execution behavior
- Return concise markdown summaries from the script JSON by default.
- Prefer these paths: `gene/<id>`, `variant/<id>`, `clinicalAnnotation`, `dosingGuideline`, and search endpoints.
- If the user needs the full payload, set `save_raw=true` and report the saved file path.

## Input
- Read one JSON object from stdin.
- Required fields: `base_url`, `path`
- Optional fields: `method`, `params`, `headers`, `json_body`, `form_body`, `record_path`, `response_format`, `max_items`, `max_depth`, `timeout_sec`, `save_raw`, `raw_output_path`
- Common PharmGKB patterns:
  - `{"base_url":"https://api.pharmgkb.org/v1/data","path":"gene/PA36679"}`
  - `{"base_url":"https://api.pharmgkb.org/v1/data","path":"clinicalAnnotation","params":{"relatedChemicals.accessionId":"PA449726","limit":10},"max_items":10}`
  - `{"base_url":"https://api.pharmgkb.org/v1/data","path":"variant/PA166158545"}`

## Output
- Success returns `ok`, `source`, `path`, `method`, `status_code`, `warnings`, and either compact `records` or a compact `summary`.
- Use `raw_output_path` when `save_raw=true`.
- Failure returns `ok=false` with `error.code` and `error.message`.

## Execution
```bash
echo '{"base_url":"https://api.pharmgkb.org/v1/data","path":"gene/PA36679"}' | python scripts/rest_request.py
```

## References
- No additional runtime references are required; keep the import package limited to this file and `scripts/rest_request.py`.
