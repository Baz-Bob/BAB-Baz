---
name: evaluate-plugin
description: "以工程师友好的方式评估本地 Codex 插件。适用于用户说「评估这个插件」「审计这个插件」「为什么得了这个分」「我应该先修什么」「帮我对这个插件做基准测试」，或在对比版本前请求全插件报告的场景。"
---

# Evaluate Plugin

Use this skill when the target is a plugin root with `.codex-plugin/plugin.json`.

## Workflow

1. Treat "Evaluate this plugin." as the default entrypoint.
2. If the request comes in as natural chat language, use `plugin-eval start <plugin-root> --request "<user request>" --format markdown` first so the user sees the routed local path.
3. Run `plugin-eval analyze <plugin-root> --format markdown`.
4. Read `Fix First` before drilling into manifest findings, nested skill findings, and code or coverage details.
5. If the plugin contains multiple skills, summarize the strongest and weakest ones explicitly.
6. If the user wants measured usage, switch to "Help me benchmark this plugin." and use the starter benchmark flow.
7. If the user wants trend data, compare two JSON outputs with `plugin-eval compare`.

## Chat Requests To Recognize

- `Evaluate this plugin.`
- `Audit this plugin.`
- `Why did this score that way?`
- `What should I fix first?`
- `Help me benchmark this plugin.`
- `What should I run next?`

## Commands

```bash
plugin-eval start <plugin-root> --request "Evaluate this plugin." --format markdown
plugin-eval analyze <plugin-root> --format markdown
plugin-eval start <plugin-root> --request "What should I run next?" --format markdown
plugin-eval compare before.json after.json
plugin-eval report result.json --format html --output ./plugin-eval-report.html
plugin-eval init-benchmark <plugin-root>
plugin-eval benchmark <plugin-root> --dry-run
```

## Reference

- `../../references/chat-first-workflows.md`
