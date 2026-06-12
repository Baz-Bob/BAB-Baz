---
name: sharepoint-site-discovery
description: "在进行文件操作前，解析正确的 SharePoint 站点、文档库和文件夹。当用户需要找到正确的站点上下文、浏览已知站点、查看文档库，或在获取或编辑文件前确定正确文件夹时触发。"
---

# SharePoint Site Discovery

Use this skill when the main job is locating the right SharePoint site, drive, or folder before file analysis or editing.

## Start Here

- Treat SharePoint discovery as site-scoped, not user-recency-scoped.
- Use `search(query="...")` for keyword search.
- Use `search(query=None, hostname=..., site_path=..., folder_path=...)` for browse mode.
- Use `get_site(...)` and `list_site_drives(...)` when the user knows the site but not the right library.

## Workflow

1. If the user names a SharePoint hostname and site path, validate them with `get_site(...)`.
2. If the site is known but the right library is not, use `list_site_drives(...)` to inspect the site-scoped document libraries.
3. If the user wants to browse a known folder or library, use `search(query=None, hostname=..., site_path=..., folder_path=...)` and inspect the immediate children.
4. If the user wants to find a file by keyword, use `search(query="...")`, then narrow with `hostname`, `site_path`, or `folder_path` when the scope is known.
5. Preserve the exact returned `url`, site, drive, and folder context so later `fetch`, `update_file`, or `upload_file` calls use the resolved destination instead of a guessed path.
6. When multiple plausible sites or libraries exist, present the candidates and explain the distinguishing context instead of picking silently.

## Output Conventions

- Name the exact site, library, and folder you resolved.
- Distinguish clearly between browse results and keyword-search results.
- When handing off to another SharePoint workflow, include the resolved `url` or the exact site and folder context that should be reused.

## Example Requests

- "Find the right SharePoint site for the launch checklist and show me the available document libraries."
- "Browse the ops site and narrow me to the folder that contains the Q2 roadmap files."
- "Search SharePoint for the pricing workbook, but keep the search inside the finance site."
