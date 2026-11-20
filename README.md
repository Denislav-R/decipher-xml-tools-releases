# Decipher XML Tools

VS Code tools for authoring Decipher survey XML, with familiar Sublime shortcuts, question generators, client parsers, templates, reusable lists, formatting and completions.

## Install

1. Get the `.vsix` installation file.
2. In VS Code open Extensions, select the `...` menu, choose **Install from VSIX**, and select the downloaded file.
3. Reload if prompted. Open an XML document and use **Decipher: Open Guide** for the searchable shortcut reference and Sublime migration help.

No custom keybindings file is needed. F1 opens the Decipher palette in focused `survey*.xml` XML editors and uses normal VS Code behavior elsewhere. Ctrl+1 creates rows, Ctrl+Alt+R makes radio questions, Ctrl+Alt+C makes checkboxes, and F8 parses the selected text or current question. Select your client with **Decipher: Change Survey Type (For Parsing)**; FocusVision uses the FV parser. Automatic save cleanup targets XML files containing `survey` in the basename. Those survey files indent with 2 spaces on Tab; change this with the `decipher.surveyTabSize` setting (`0` leaves it to VS Code).

## Recommended settings for Sublime users

Press **Ctrl+,**, search for the name, and change it on the **User** tab. The extension does not change these for you.

- **Editor: Smooth Scrolling** — enable it so Find (Ctrl+F, Enter/F3) scrolls visibly to each match, as in Sublime.
- **Editor: Multi Cursor Modifier** — the default is **alt** (Alt+click adds cursors). Choose **ctrlCmd** for Sublime-like **Ctrl+click** cursors; Go to Definition / Open Link then move to Alt+click.

## Optional VS Code editor settings

These are personal VS Code preferences. The extension does not change them automatically.

- **Match whole words:** press **Ctrl+F**, enable **Match Whole Word** (the **ab** button), then press **Esc**. This keeps selected-text matches out of longer words and also affects Find and Ctrl+D matching.
- **Highlight only selected text:** press **Ctrl+,**, search **Editor: Occurrences Highlight**, and choose **off**. Keep **Editor: Selection Highlight** enabled so matching text is still highlighted when selected, rather than merely when the cursor is placed on a word.
- **Wrap long lines:** press **Ctrl+,**, search **Editor: Word Wrap**, and choose **on** on the **User** tab to apply it to all files. Lines wrap at the editor edge without changing the file contents. **Alt+Z** toggles wrapping for the current editor.

See [VS Code settings](https://code.visualstudio.com/docs/configure/settings) for user, workspace and language-specific preferences.

## Survey Issues

Saving a `survey*.xml` file checks it: XML errors, simple Python/JavaScript mistakes and the survey checks (values, groups, `$(` in styles and more). Everything found is listed in **Survey Issues** at the top of the **Decipher Tools** sidebar, for the survey in the active tab, with the line number; click an entry to go there. After a save with errors the list opens by itself. Every check can be turned off: right-click an entry, or see the `decipher.surveyChecks*` and `decipher.issuesView.autoOpen` settings.

## Personal Library

Open a `survey*.xml` file in XML language mode to show the Personal Library panel. Add your own template, choose insertion, selection or question label/title input, and preview before saving. Click a template row to insert it; use the pencil to edit. The folder button opens your library storage.

The panel stays available while a survey XML tab is open. Your library is stored separately from the extension, so installing updates keeps your entries. Templates can contain survey Python, JavaScript and XML; the extension inserts that content without executing it.

## Updates

The extension checks for updates on startup, at most once daily. Choose **Install update** in the notification and it downloads, verifies and installs the new version; then choose **Reload now**. If that fails, **Download VSIX** opens the manual download for **Install from VSIX**. Use **Decipher: Check for Updates** to check immediately. Automatic checks are enabled by default. To change this, open VS Code Settings and search for `decipher.updates.enabled`.

All authoring runs locally. Update checks request GitHub release metadata and never send your questionnaire or XML. Private releases require your own GitHub account with access; sign in through the manual update check when prompted. A public releases repository requires no sign-in.

If an older Forsta extension identity is installed, disable/uninstall it once to avoid duplicate commands. Later versions of Decipher XML Tools update the same extension identity.

## Current limits

- **QArts:** the QArts tools are not fully brought over from Sublime yet; some work differently or are missing.
- **PRF:** you can write PRF surveys with the usual commands and completions, but PRF parsing is not available.
- **Older file encodings:** files saved in an older encoding (such as ISO-8859-1) are opened and saved with VS Code's own encoding controls (click the encoding in the status bar).

See the built-in guide for details.

The runtime is bundled and obfuscated; editable TypeScript is excluded. This is not a guarantee against reverse engineering. The download repository contains installation packages and release notes only. Dependency license notices are included in the extension.
