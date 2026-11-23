# Trailhead Study Buddy

A Claude plugin that copies the Salesforce Trailhead unit open in your Chrome tab into a structured markdown note, word for word.

It is an extractor, not a summarizer. The note keeps the unit's own text, headings, lists, tables, and code, so what you study later is what Trailhead actually said.

## What you get

Say `/capture` (or "capture this unit") with a Trailhead unit open. Claude returns one markdown block:

```markdown
---
source_type: trailhead
source_url: <page URL>
trail: <trail name, or null>
module: <module title>
module_slug: <from the URL>
unit: <unit title>
unit_slug: <from the URL>
unit_number: <position in the module>
captured_at: <YYYY-MM-DD>
captured_by: claude-in-chrome
complete: true
---

# <Unit title>

<unit content, verbatim>

## Knowledge check
## Hands-on challenge
## Not captured
## Learner notes
```

## Capture rules

- Instructional text is reproduced verbatim: nothing summarized, reworded, reordered, or added.
- Images and videos become one-line placeholders such as `[Image: ...]` and `[Video: ...]`.
- Quiz questions are copied with every option. An answer is included only when the page shows it.
- Navigation, footers, badges, points, and cookie banners are skipped.
- A unit too long to finish stops at a heading, sets `complete: false`, and lists the missed headings under `## Not captured`.

The full instructions are in [skills/capture/SKILL.md](skills/capture/SKILL.md).

## Requirements

- Claude Code or the Claude desktop app
- The Claude in Chrome extension, which is how Claude reads the page

## Install

Clone the repository:

```bash
git clone https://github.com/tedirland/trailhead_study_buddy.git
```

Then pick one:

- **One session:** start Claude Code with the plugin loaded.

  ```bash
  claude --plugin-dir ./trailhead_study_buddy
  ```

- **Every session:** copy the skill into your personal skills folder.

  ```bash
  cp -R trailhead_study_buddy/skills/capture ~/.claude/skills/
  ```

## Repository layout

```text
.claude-plugin/plugin.json   Plugin name and description
skills/capture/SKILL.md      The capture instructions
```
