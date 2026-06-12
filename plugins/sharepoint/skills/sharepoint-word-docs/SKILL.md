---
name: sharepoint-word-docs
description: "编辑 SharePoint 托管的 Word `.docx` 文件，同时保留文档结构和样式。适用于用户希望更新 SharePoint 中真实 Word 文档（而非将其汇总为纯文本）的场景。"
---

# SharePoint Word Docs

## Overview

Use this skill for `.docx` edits that start from SharePoint. Treat the file as a real Word package, not as extracted text, and preserve the existing document structure and styling unless the user explicitly accepts formatting loss.

## Core Workflow

1. Search for the file and identify the exact target by title, path, and file type.
2. Fetch extracted text once to verify it is the right document and to locate the target section.
3. Fetch the raw `.docx` with `fetch(download_raw_file=true)` before editing.
4. Edit locally with `python-docx` or equivalent OOXML-aware local tooling so the original Word package remains intact.
5. Ensure that the upload path can preserve a normal styled Word package before overwriting the original.
6. Write the revised file back with `update_file` using the exact drive-root-relative path from SharePoint metadata.
7. Re-fetch and verify both:
   - the intended text or section change
   - the expected structure or styling when possible

## Safety

- Do not replace a styled `.docx` with plain text output.
- Do not replace a styled `.docx` with a minimal regenerated package merely to make upload succeed unless formatting loss is already acceptable from the request context.
- Treat inline base64 binary upload as potentially brittle for richer `.docx` packages. If the write path looks unsafe, stop and explain the formatting risk rather than silently degrading the file.
- If the first overwrite attempt returns `itemNotFound`, inspect the folder items and use the exact root-relative path from SharePoint metadata.

## Verification

- Content verification alone is not enough for existing styled documents.
- Check heading structure, spacing, and style preservation when possible.
- If you can only validate text content, say so explicitly and note the remaining formatting risk.
