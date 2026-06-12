---
name: improve-skill
description: "将 plugin-eval 的评估结果转化为具体的 Codex 技能重写方案。适用于用户已完成技能评估、希望 Codex 帮助改进，尤其是在问完「先修什么」之后。"
---

# Improve Skill

Use this skill after `plugin-eval` has already produced findings for a local skill.

## Workflow

1. Run `plugin-eval analyze <skill-path> --brief-out <brief.json>`.
2. Read the improvement brief and group work into required fixes versus recommended fixes.
3. Apply the `skill-creator` guidance from `/Users/benlesh/.codex/skills/skill-creator/SKILL.md`.
4. Re-run the evaluation and compare before and after outputs.

## Chat Requests To Recognize

- `Improve this skill based on the evaluation.`
- `Rewrite this skill using the plugin-eval findings.`
- `What should I fix first in this skill?`

## Focus Areas

- reduce trigger and invoke token costs
- keep `SKILL.md` compact
- move bulky details into references or scripts
- improve trigger descriptions
- fix broken links and manifest/frontmatter issues

## Commands

```bash
plugin-eval analyze <skill-path> --brief-out ./skill-brief.json
plugin-eval compare before.json after.json
```

## Reference

- `../../references/chat-first-workflows.md`
