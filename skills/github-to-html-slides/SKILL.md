---
name: github-to-html-slides
description: >-
  Reads a GitHub repository document via GitHub MCP and generates a self-contained
  HTML slide deck with keyboard/click navigation, continuous page numbers, and
  working images. Use when the user asks to turn a GitHub doc/README/notes into
  an HTML PPT, slides, or presentation, or when invoking github-to-html-slides.
disable-model-invocation: true
---

# GitHub → HTML Slides

## When to use

User wants an HTML presentation generated from a GitHub file (README, notes, summary, etc.).

## Prerequisites

- GitHub MCP available (`get_file_contents`, optionally `create_or_update_file`)
- Know `owner`, `repo`, and source `path` (ask if missing)

## Workflow

Copy and track:

```
Progress:
- [ ] 1. Read source doc from GitHub
- [ ] 2. Outline slides from content
- [ ] 3. Write self-contained HTML PPT
- [ ] 4. Verify navigation / images / page numbers
- [ ] 5. Deliver path + how to open
```

### 1. Read source

Use GitHub MCP `get_file_contents` with `owner`, `repo`, `path`.
Summarize structure: title, sections, key bullets, any image URLs.

### 2. Outline slides

Map content to slides (one idea per slide):

1. Title
2. Agenda / overview (optional)
3. One section → one or few slides
4. Summary / takeaways
5. End / Q&A (optional)

Aim for 6–15 slides unless the doc is very long.

### 3. Generate HTML

Write a **single self-contained `.html` file** (inline CSS + JS). Default path:

- Personal/local: `./slides/<topic>-slides.html` or user-specified path
- Or push to GitHub with `create_or_update_file` if user asks to publish

**Required behavior:**

| Requirement | Implementation |
|-------------|----------------|
| Page navigation | Arrow keys, click left/right zones or buttons, optional dots |
| Images load | Absolute `https://` URLs; no broken relative paths |
| Continuous page numbers | Show `当前页 / 总页数` on every slide |

**Design defaults (unless user specifies otherwise):**

- Full-viewport slides (`100vw` × `100vh`)
- Clear typography hierarchy; avoid generic Inter/Roboto/Arial stacks — pick expressive web fonts via Google Fonts CDN
- One composition per slide; no dashboard clutter
- Strong title hierarchy; short bullets
- Subtle gradient or atmospheric background (not flat white only)
- At least light transition between slides
- Mobile-usable: large tap targets for prev/next

### 4. Verify before delivery

- [ ] Prev/next and ←/→ change slides
- [ ] Counter matches `index+1 / total` and stays continuous
- [ ] Every `<img>` uses a reachable absolute URL (or omit images)
- [ ] Title slide states source: `owner/repo/path`

### 5. Deliver

Tell the user:

1. File path (and GitHub URL if published)
2. Open with browser (double-click or Live Preview)
3. How to regenerate: name this skill + give a different `path`

## SOP

Follow [SOP.md](SOP.md) for the standard operating procedure checklist.

## Examples

**Generate from repo notes:**

> 用 github-to-html-slides，把 yidiandian210/mcp-homework 的 learning-notes.md 生成 HTML PPT

**Generate again with another doc:**

> 再用这个 Skill，把 study-summary.md 生成另一份 HTML PPT
