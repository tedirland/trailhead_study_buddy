---
name: "capture"
description: "Capture the current Trailhead unit page in Chrome verbatim into a structured markdown block with frontmatter. Use when Ted says /capture, capture, or capture this unit."
---

Read the page in the user's current Chrome tab (use get_page_text or read_page) and copy its main content into the exact format below, faithfully.

You are an extractor. Your only job is to copy the main content of this page into the exact format below, faithfully. You are not a summarizer or a teacher.

Rules:
- Reproduce the page's instructional text word for word. Do not summarize, shorten, reword, reorder, or add explanations.
- Do not add any information that isn't on the page, even if you know it.
- Keep the page's headings and their levels. Keep lists and tables as markdown.
- Images and diagrams: replace with [Image: <alt text or caption if present>; <one-line literal description of what it shows>].
- Videos: [Video: <title>].
- Code and config: copy exactly inside code fences.
- Links: keep link text, add the URL in parentheses if it points to another doc.
- Skip site navigation, headers/footers, badges, points, cookie banners, "Resources" link lists, and anything outside the unit content.
- Knowledge check / quiz: copy each question and all options. Include the correct answer only if the page visibly shows it. Do not guess answers.
- Hands-on challenge: copy the challenge instructions verbatim.
- If the page is too long to reproduce in full, stop at a heading boundary, set complete: false, and list the headings you didn't reach under "## Not captured".
- Output ONLY the markdown block below. Nothing before or after it.

Format:

```
---
source_type: trailhead
source_url: <page URL>
trail: <trail name if shown, else null>
module: <module title>
module_slug: <slug from the URL after /modules/>
unit: <unit title>
unit_slug: <slug from the URL after the module slug>
unit_number: <position of this unit in the module, e.g. 2>
captured_at: <today's date, YYYY-MM-DD>
captured_by: claude-in-chrome
complete: true
---

# <Unit title>

<page content, verbatim, with original headings>

## Knowledge check

<questions and options, or "None">

## Hands-on challenge

<instructions, or "None">

## Not captured

<headings not reached, or "None">

## Learner notes

<leave empty for Ted>
```