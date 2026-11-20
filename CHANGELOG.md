# Release notes

## 0.1.6 - 2026-11-20

- **Survey Issues** in the sidebar (the Decipher icon, now called **Decipher Tools**): one list of everything wrong in the survey you're looking at, XML errors, Python/JS mistakes and survey checks, with the line number. Click an entry to jump to it. After a save with errors it opens by itself and puts you straight back in the editor; set `decipher.issuesView.autoOpen` to `issues` (warnings too) or `never`. A number on the sidebar icon shows how many issues there are.
- **Survey checks on save:** 20 rules catch common survey mistakes and things Decipher refuses to compile or breaks on, for example some options with `value=` and others without, `values="order"`, values on checkbox rows, a rating scale without values, `$(` or a line-start `@media` in a style, `rows.order` without `shuffle="rows"`, a comment above `<survey>`. They're listed in **Survey Issues** (below) and the Problems panel (Ctrl+Shift+M), and the status bar sums them up after each save. Want a popup for them too? Set `decipher.surveyCheckPopup` to `errors` (or `all` for warnings as well). Don't want one? Right-click it in Survey Issues (or use the light bulb) and choose **Turn off this check**; **Decipher: Turn Survey Checks Back On** brings it back. `decipher.surveyChecks` turns them all off. Quick fixes write `$ (` and escape `\@media`.
- Clearer error checks on save: a missing closing quote is reported once on its attribute, unclosed tags where they open, and code (`&`, `<`, `</style>` inside CDATA) no longer counts as an XML error.
- New checks on save, both on by default: text typed outside any tag (`decipher.strayTextCheck`), and simple Python/JavaScript mistakes such as a missing `:` after `if`/`for`, unbalanced brackets, unclosed strings or a nested `<exec>` (`decipher.codeSyntaxCheck`).
- The error popup closes itself on your next clean save and has Go to Line / Next / Previous / Close links. Prefer the old one? Set `decipher.errorPopup` to `"buttons"`.
- Better suggestions: the latest DQ versions inside `uses="…"`, that DQ's attributes on its question (or after typing e.g. `cardsort:`), `<susp` gives `<suspend/>`, Enter after a Python `if …:` line just makes a new line, and `.val`-style Python suggestions beat Emmet again.
- New Survey offers FocusVision, Repdata and codexmr (Kantar and M3 templates are removed). Run **Decipher: Set Template Keys** once to save your ReDem API key securely on your PC; the Mindline template then fills it in.
- New Survey: all templates use compat 155, and there are new survey templates.
- Ctrl+/ inside a multi-line `<!-- … -->` comment now removes that comment.
- Sticky scroll can be turned on in Settings: search for `decipher.stickyScroll`.
- Personal Library: Collapse All turns into Expand All.
- Decipher directives such as `\@if` / `\@endif` are coloured as a whole line in CSS/JS/Python (`decipher.directiveColor`, green by default; empty = your theme's colour). `decipher.italicAttributes` set to false stops attribute names showing in italics. Both work through one rule the extension adds to your `editor.tokenColorCustomizations` setting; your own rules are kept.
- Fixes: `&&` in some CDATA styles is no longer escaped on save, and several highlighting leaks (comments turning non-gray, half-typed Python colouring the rest of the file) are gone.

## 0.1.5 - 2026-10-27

- One-click updates: from now on the update notification's **Install update** downloads, verifies and installs the new version; then choose **Reload now**. This version itself still installs the usual way.
- See the survey's structure in the **Outline** view and the breadcrumbs above the editor: blocks, loops, `if`s and questions as a nested tree, each with its `cond`. Sticky scroll is off for XML by default; **Decipher: Toggle Sticky Scroll (XML)** turns it on.
- Keep Thai, accented and other non-ASCII text readable: turn off `decipher.escapeNonAscii` and Escape-On-Save still escapes bare `&`.
- **Decipher: Decode Character References** turns `&#3648;`-style references back into real characters, and the optional `decipher.decodeOnOpen` setting does it when a survey opens.
- Search your Personal Library templates with the new search button in the panel header.

## 0.1.4 - 2026-10-14

- Command names now match the Sublime palette, for example **Decipher: Add values (vals)**, **Decipher: Add groups** and **Decipher: Add exclusive**. Formatting, QArts and Run Bright Parser commands also appear in the F1 Decipher palette.
- Suggest labels from your survey: question labels in `cond`, `rowCond`, `colCond`, `choiceCond` and `onLoad` (and row labels after `Q1.`), in `shuffleBy`, `below`, `rightOf` and `keepWith`; `<res>` labels after `res.` in Python and in `${res.` pipes; define lists in `<insert source>`.
- Fix Python suggestions in `<exec>`/`<validate>` losing to Emmet: `Q6.r` suggests `.rows` instead of becoming `<Q6 class="r">`. Words already used in the survey are suggested too, as in Sublime.
- Add the Sublime QArts `qa:` attribute completions for surveys using `qastyler`.
- Fix the right-click QArts tool items, and add **Open Knowledge Base link** and **Open Style Library link**.
- Tab indents survey XML files by 2 spaces (`decipher.surveyTabSize`; `0` leaves it to VS Code). Other XML files are unaffected.

## 0.1.3 - 2026-10-10

- Sublime-style editing in XML: Ctrl+Shift+A selects tag contents at every cursor, Ctrl+M jumps between brackets, Ctrl+Shift+M selects inside them, and Ctrl+L selects whole lines (Ctrl+L then Ctrl+I still makes list items).
- Underline the matching tag names and brackets at the cursor instead of VS Code's boxed highlight, and stop treating XML `<` `>` as brackets.
- Fix Ctrl+/ in `<exec>`, `<validate>` and `<style>` blocks, and highlight JavaScript inside `wrap="ready"` CDATA styles.
- Guide: recommended Sublime-like settings (smooth scrolling, Ctrl+click cursors) and opening files side by side.

## 0.1.2 - 2026-10-06

- Restore CSS brace/Enter indentation and cursor placement inside survey XML CDATA style blocks.
- Add CSS Emmet suggestions and Tab expansion (`wid`, `w50`, and other CSS abbreviations) while retaining XML mode and normal Tab/snippet behavior.
- Document optional whole-word selection matching, selection-only highlighting and long-line wrapping settings.

## 0.1.1 - 2026-10-05

- Add a Personal Library sidebar with categories, row-click template insertion, an Add/edit form, preview, and selection or question label/title substitution.
- Keep personal templates in VS Code extension storage across updates, with a folder shortcut in the panel.
- Restore theme-aware XML attribute and quoted-value highlighting on embedded Python/JavaScript/CSS opening tags.
- Restrict F1 / the Decipher command palette to focused XML files named `survey*.xml`; restore normal F1 elsewhere.

## 0.1.0 - 2026-10-04

- Introduce Decipher XML Tools, keeping the built-in Decipher commands and all 59 original Sublime shortcuts.
- Include question/element generators, five client parsers, reusable lists, agency templates, styles, formatting, loops, mutators and utilities.
- Include a searchable Markdown guide inside VS Code, with Sublime-to-VS Code keyboard and multi-cursor help.
- Add optional daily GitHub release checks and **Decipher: Check for Updates**.
- Ship a bundled, minified and obfuscated runtime, excluding editable TypeScript and source maps.

QArts parity is deferred. PRF authoring is available; its parser is not included. Use VS Code's file encoding controls for legacy files. This release runs locally; update checks request GitHub release metadata only.
