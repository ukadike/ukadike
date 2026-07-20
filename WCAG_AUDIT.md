# Accessibility Audit — GitHub Profile Markdown

Scope: `README.md`, `WHY-OMOLUABI.md`, `docs/REPO_AUDIT.md`.

**Note on scope:** Full WCAG 2.1 AA applies to standalone web applications —
things like focus management, ARIA state, color-contrast measurement on
rendered CSS, and keyboard-trap testing don't strictly apply here, since this
is not a standalone web app; it's Markdown rendered by GitHub's own
stylesheet on `github.com/ukadike`. This audit holds the content to the
*intent* of WCAG for the things an author actually controls in Markdown:
meaningful alt text, logical heading structure, descriptive link text, no
color-only meaning, and plain-language clarity — since screen-reader users do
browse GitHub profile pages.

## Method

- Read every Markdown file in full.
- Extracted and reviewed all `![alt](...)` and `<img alt="...">` embeds.
- Viewed each of the five embedded source images directly and compared them
  against their existing alt text for factual accuracy (not just presence).
- Extracted all heading lines (`grep '^#+ '`) per file to check hierarchy.
- Extracted all Markdown links to check link text.
- Searched for raw HTML (`<div>`, `<img>`, `<details>`, `<summary>`, tables)
  and for inline `style=`/`color:`/badge/shield markup that could carry
  color-only meaning.

## Findings

### 1. Image alt text — checked, no fixes needed

All five image embeds are in `README.md` (lines 3, 42, 105, 113, 154).
`WHY-OMOLUABI.md` and `docs/REPO_AUDIT.md` contain no images.

| File:line | Image | Result |
|---|---|---|
| README.md:3 | `adekemi-headband.jpeg` | Alt text accurate against the photo (portrait, headwrap, looking at camera). No change. |
| README.md:42 | `assets/ssl-ecosystem.png` | Alt text accurate — verified diagram content (6 branches, guiding principles, focus areas) matches the image and matches the text that follows it in the doc. No change. |
| README.md:105 | `assets/omoluabi-spec.png` | Alt text accurate against the spec-sheet image (views, labelled parts, principles, colorways). No change. |
| README.md:113 | `assets/omoluabi-device.png` | Alt text accurate against the device/web-engine poster. No change. |
| README.md:154 | `assets/umada-scene.png` | Alt text accurate against the painted scene (figures, lighthouse, C.A.R.F. coat marking). No change. |

**Status: 0 open, 0 fixed — all 5 embeds already had meaningful, accurate,
non-filename alt text before this audit; verified rather than rewritten.**

Two image files exist in the repo but are not embedded in any Markdown file
(`images/adekemi-rooftop.JPG`, `images/omoluabi-system.png`, plus a duplicate
root-level `adekemi-rooftop.JPG`). Not in scope for alt-text review since
they aren't rendered anywhere; already flagged for Kemi's review in
`docs/REPO_AUDIT.md`.

### 2. Heading hierarchy — checked, no fixes needed

- `README.md`: one H1 (line 9), then H2/H3 levels used in order with no
  skipped levels (H1 → H2 → H3 → H2 → H2 → H3×5 → H2 → H2 → H2 → H2).
- `WHY-OMOLUABI.md`: one H1 (line 1), all subsections are H2. No skips.
- `docs/REPO_AUDIT.md`: one H1 (line 1), all subsections are H2. No skips.

**Status: 0 open, 0 fixed.**

### 3. Link text — checked, no fixes needed

Every link in the three files:

- `README.md:33` — `[**Why Omoluabi**](./WHY-OMOLUABI.md)`
- `README.md:201` — `[github.com/ukadike](https://github.com/ukadike)`
- `README.md:202` — `[@kemi.systems](https://instagram.com/kemi.systems)`
- `WHY-OMOLUABI.md:48` — `[Small Systems Lab](./README.md)`

All are descriptive out of context. No bare "here"/"this link"/"click here"
instances found in any file.

**Status: 0 open, 0 fixed.**

### 4. Color-only meaning — checked, no fixes needed

No inline `style=`, `color:`, badge, or shield markup exists in any of the
three Markdown files. The one place color carries information is *inside*
`assets/ssl-ecosystem.png` itself (each of the six branches has a distinct
accent color) — but each branch is also distinguished by an icon and a text
label, and the image's alt text spells out all six branches by name, so no
meaning depends on color alone.

**Status: 0 open, 0 fixed.**

### 5. Raw HTML — checked, no fixes needed

Raw HTML present is limited to `<div align="center">`, `<img>` (covered in
§1), `<br>`, and `<sub><em>...</em></sub>` caption wrappers. No `<table>`,
`<details>`, or `<summary>` elements exist. No semantic issues found.

**Status: 0 open, 0 fixed.**

### 6. Plain-language clarity — flagged for awareness, not rewritten

Per instruction, prose voice was not rewritten. Two things worth Kemi's
awareness (open, no action taken):

- **README.md / WHY-OMOLUABI.md — thematic terms used without a plain-language
  gloss on first use:** "editorial intelligence," "rule-based intelligence,"
  and "operations of care" are house terms central to the SSL/Omoluabi voice.
  Most are explained close to first use (e.g. the Ancient Geometry list
  immediately unpacks each term), but "operations of care" (README.md:51) and
  the standalone phrase "editorial intelligence" (README.md:98) are not
  glossed at their point of use. Left open — this is a voice/framing choice,
  not an accessibility defect, and ground rule 3 says not to rewrite prose
  voice beyond what accessibility strictly requires.
- **README.md — decorative `&middot;` separators (11 occurrences, e.g. lines
  9, 11, 77, 96, 100, 168, 207):** a common GitHub-profile styling pattern.
  Screen readers typically announce these as "middle dot" between items,
  which is mildly verbose but not a WCAG violation and not color- or
  hover-dependent. Left open as a low-priority style note only — no
  compliance issue.

Abbreviations that *are* already spelled out correctly on first use and
required no flag: CIDP (`WHY-OMOLUABI.md:15`, `README.md:29`), ITP
(`README.md:184`).

## Summary counts

| Category | Checked | Fixed | Open |
|---|---|---|---|
| Image alt text | 5 embeds | 0 | 0 |
| Heading hierarchy | 3 files | 0 | 0 |
| Link text | 4 links | 0 | 0 |
| Color-only meaning | 3 files | 0 | 0 |
| Raw HTML semantics | 3 files | 0 | 0 |
| Plain-language jargon | 3 files | 0 | 2 (flagged, not fixed — voice/style, not defects) |

**Total: 0 accessibility defects found; 2 non-blocking style notes flagged
for awareness.** This repository's Markdown was already in strong shape
going into this audit — no image, heading, link, or color-only issues
required correction.
