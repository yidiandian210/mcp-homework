# SOP: GitHub Doc to HTML PPT

Standard operating procedure. Follow this checklist every time `github-to-html-slides` is invoked.

## Inputs

| Param | Required | Meaning | Example |
|------|----------|---------|---------|
| owner | yes | GitHub user/org | `yidiandian210` |
| repo | yes | Repository name | `mcp-homework` |
| path | yes | Source document path | `learning-notes.md` |
| output | no | Output HTML path | `slides/learning-notes-slides.html` |
| publish | no | Push to GitHub | `true` / `false` (default false) |

If params are missing, ask the user. Do not guess private paths.

## Steps

### Step A - Read document

1. Call GitHub MCP: `get_file_contents`
2. Extract body (title, sections, lists, image URLs)
3. Confirm in one line: generating HTML PPT from `owner/repo/path`

### Step B - Split into slides

1. Title slide: document title + source repo
2. Content slides: one idea per slide
3. Closing slide: 3-5 takeaways
4. Record total pages `N`; numbers run 1..N continuously

### Step C - Produce HTML

1. Generate a **single-file** HTML (inline CSS/JS)
2. Implement:
   - Prev / Next buttons
   - Keyboard Left / Right arrows
   - Page counter as `current / N`
3. Images only with absolute URLs; skip images if none are reliable
4. Save to `output`; if `publish=true`, also `create_or_update_file` to the repo

### Step D - Self-check

| Check | Pass criteria |
|-------|---------------|
| Navigation | Buttons and arrow keys both work |
| Page numbers | Correct on every slide, 1..N no gaps |
| Images | All load, or this deck has no images |
| Readability | Clear hierarchy, first viewport not cluttered |

### Step E - Deliver

Return to the user:

1. Local or repo HTML path
2. How to open (open the file in a browser)
3. Tip: change `path` and invoke this Skill again for another deck

## Failure handling

| Case | Action |
|------|--------|
| MCP read fails | Check owner/repo/path; ask user to verify token scopes |
| Doc nearly empty | Still make at least 3 slides (title / empty note / end) and say content was thin |
| No output path | Default `slides/<source-basename>-slides.html` |

## Regenerate (Homework Task 03)

Same Skill, only change source `path` (or repo). Repeat Step A-E. Do **not** make the user re-teach the workflow.
