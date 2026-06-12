---
name: evaluate-skill
description: "以工程师友好的方式评估本地 Codex 技能。适用于用户说「评估这个技能」「分析一下 game dev 技能」「审计这个技能」「为什么得了这个分」「我应该先修什么」，或在基准测试前请求技能专项报告的场景。"
---

# Evaluate Skill

Use this skill when the target is a local skill directory or `SKILL.md` file.

## Workflow

1. Treat "Evaluate this skill." as the default entrypoint.
2. If the user names a skill instead of giving a path, resolve it locally first, preferring `~/.codex/skills/<skill-name>` and then repo-local `skills/<skill-name>`.
3. If the user says the request in natural language first, use `plugin-eval start <skill-path> --request "<user request>" --format markdown` to show the routed path clearly.
4. Run `plugin-eval analyze <skill-path> --format markdown`.
5. Review `At a Glance`, `Why It Matters`, `Fix First`, and `Recommended Next Step` before drilling into details.
6. Explain which findings are structural, which are budget-related, and which are code-related.
7. If the user asks for an "analysis" of the skill, do not stop at the report. Also run `plugin-eval init-benchmark <skill-path>` and show the setup questions for refining the starter scenarios in `.plugin-eval/benchmark.json`.
8. If the user wants real usage numbers, switch to "Measure the real token usage of this skill." and run the benchmark flow.
9. After observed usage is available, use `plugin-eval measurement-plan <skill-path> --observed-usage <usage.jsonl> --format markdown` to recommend what to instrument or improve next.
10. If the user wants a rewrite plan, route to `../improve-skill/SKILL.md`.

## Skill-Specific Priorities

- frontmatter validity
- `name` and `description` quality
- progressive disclosure and reference usage
- broken relative links
- oversized `SKILL.md` or descriptions
- helper script quality for TypeScript and Python files

## Chat Requests To Recognize

- `Evaluate this skill.`
- `Give me an analysis of the game dev skill.`
- `Audit this skill.`
- `Why did this skill score that way?`
- `What should I fix first?`
- `Measure the real token usage of this skill.`

## Commands

```bash
plugin-eval start <skill-path> --request "Evaluate this skill." --format markdown
plugin-eval analyze <skill-path> --format markdown
plugin-eval explain-budget <skill-path> --format markdown
plugin-eval measurement-plan <skill-path> --format markdown
plugin-eval init-benchmark <skill-path>
plugin-eval benchmark <skill-path> --dry-run
```

## Reference

- `../../references/chat-first-workflows.md`
