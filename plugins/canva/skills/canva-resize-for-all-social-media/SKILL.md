---
name: canva-resize-for-all-social-media
description: "将 Canva 设计调整为标准社交媒体格式，并准备可直接导出的成果。适用于用户希望将一个 Canva 设计适配到多个社交平台（如 Facebook、Instagram、LinkedIn），特别是希望一次性生成所有变体时。"
---

# Canva Resize For Social Media

## Overview

Use this skill to take one Canva design and create a multi-platform set of resized variants. Identify the source design, generate the requested social formats, export each version, and present the results in a scan-friendly way.

## Preferred Deliverables

- A confirmed source design with the right title and edit context.
- Resized variants for the requested social platforms.
- Direct export links and Canva edit links for each successful output.

## Workflow

1. Identify the source design from a design ID, Canva URL, design name, or the current conversation context.
2. Confirm the source design exists and is accessible before starting any resize work.
3. Resize the design into the standard target formats for Facebook post, Facebook story, Instagram post, Instagram story, and LinkedIn post. Run independent resize operations in parallel when the tool flow supports it.
4. Continue with the formats that succeed even if one or more resize attempts fail.
5. Export each successful resized design as a high-quality PNG and collect the download links.
6. Present the finished set grouped by platform, including both the PNG download link and the Canva edit link.

## Write Safety

- Keep the original design unchanged and work from resized copies.
- If a name search returns multiple designs, identify the right one before resizing.
- Use exact target dimensions for each platform rather than approximations.
- Report partial failures clearly instead of hiding them behind a generic success message.

## Output Conventions

- Lead with a short summary of which formats were created successfully.
- List each platform separately with its dimensions, export link, and edit link.
- Mention when two outputs share the same dimensions, such as Facebook Story and Instagram Story.
- If some formats fail, separate successes from failures so the user can act quickly.

## Example Requests

- "Resize this Canva design for Facebook, Instagram, and LinkedIn."
- "Make all the social versions of this campaign graphic."
- "Take my flyer design and export all the social post sizes."
- "Resize this Canva link for every major social format."

## Light Fallback

If the source design cannot be found or exported, say that Canva access may be unavailable or scoped to the wrong design and ask the user to reconnect or identify the exact design to use.
