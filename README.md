# MDPrint

A private, local-first Markdown reader and PDF exporter. Write or open a `.md` file, read it without the syntax noise, and export it to PDF. Nothing is uploaded anywhere, and it works with no internet connection.

No build step, no npm, no server. Open `index.html` in a modern browser.

## Privacy and offline use

- All libraries and fonts are bundled in `src/vendor/`. The app makes no network requests.
- `index.html` sets a Content Security Policy (`default-src 'none'`, `connect-src 'self'`), so the browser itself blocks the page from sending data to other servers.
- Drafts are kept in your browser's `localStorage` and never leave your machine.
- The CSP still allows `'unsafe-inline'` and `'unsafe-eval'` for scripts, because the app code is inline and Mermaid uses `eval`.

## Features

- Split view: Markdown editor on the left, live preview on the right, with a draggable splitter (double-click to reset to 50/50). Stacks vertically on narrow screens.
- GitHub Flavored Markdown: tables, task lists, strikethrough, autolinks, blockquotes.
- Syntax highlighting (highlight.js) with language labels and a copy button on code blocks.
- Math with KaTeX: inline `$E = mc^2$` and display `$$ ... $$`.
- Mermaid diagrams from fenced `mermaid` blocks.
- PDF export through the browser's print engine, which gives vector output with selectable text. The print stylesheet sets 18mm margins, hides the UI, avoids page breaks inside code blocks, tables, images and diagrams, wraps long code lines, and prints links as plain text.
- Light and dark themes; dark mode carries over to the PDF.
- Auto-save of the draft, filename, theme and splitter position.
- Open `.md` / `.txt` files with the button or by drag and drop.
- Copy the rendered HTML to the clipboard.
- Word count, character count and reading time.

## Usage

1. Open `index.html` in Chrome, Edge, Firefox or Safari.
2. Type, paste, or open a Markdown file.
3. Click **Export PDF** (or press Ctrl+P / Cmd+P).

In the print dialog:

- Destination: Save as PDF.
- Margins: Default (the stylesheet already sets 18mm).
- Background graphics: on, if you want code block backgrounds, table shading or dark mode colors.
- Headers and footers: off, for a clean page without date and URL stamps.

## Shortcuts

| Shortcut | Action |
| :--- | :--- |
| Tab | Indent selected lines by 2 spaces |
| Shift + Tab | Dedent selected lines by 2 spaces |
| Ctrl / Cmd + P | Print / export PDF |
| Double-click splitter | Reset to 50/50 |

The **Sample** button replaces the draft with a demo document covering every feature.

## Project structure

```
index.html          Application (HTML, CSS and JS in one file)
src/vendor/         Bundled libraries and fonts
README.md
```

## Bundled libraries

| Library | Version | Purpose |
| :--- | :--- | :--- |
| [marked](https://marked.js.org/) | 15.0.7 | Markdown parser |
| [highlight.js](https://highlightjs.org/) | 11.9.0 | Code highlighting |
| [KaTeX](https://katex.org/) | 0.16.10 | Math rendering |
| [marked-katex-extension](https://github.com/UziTech/marked-katex-extension) | 5.1.0 | KaTeX integration for marked |
| [Mermaid](https://mermaid.js.org/) | 10.9.1 | Diagrams |
| [Inter](https://rsms.me/inter/), [JetBrains Mono](https://www.jetbrains.com/lp/mono/) | latin subsets | Fonts, via Fontsource |

To update a library, replace its file in `src/vendor/` with the new release.

## Comparison with other tools

Approximate, based on default setups; check each tool for current details.

| | MDPrint | Typora | Obsidian | StackEdit | Dillinger | VS Code + extensions |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Setup | None, open one HTML file | Install app | Install app, plugins for extras | Web app, account for sync | Web app | Install editor and extensions |
| Offline | Yes | Yes | Yes | Limited | No | Yes |
| PDF export | Vector, via browser print | Vector, built in | Built-in export; extras via plugins | Rendered by a server-side service | Basic | Via extension |
| Math (KaTeX/LaTeX) | Built in | Built in | Built in | Built in | No | Via extension |
| Mermaid | Built in | Built in | Built in | Yes | No | Via extension |
| Dark mode | Yes, carries into the PDF | Yes | Yes | Yes | Yes | Yes |
| Editing style | Source plus live preview | WYSIWYG | Source or live preview | Source plus live preview | Source plus live preview | Source plus preview |
| Single portable file | Yes, plus a `src/vendor/` folder | No | No | No | No | No |
| Where documents live | Your browser only | Local files | Local vault | Browser, optionally cloud-synced | Browser, optionally cloud-linked | Local files |
| Cost | Free | Paid | Free for personal use | Free | Free | Free |
| Install size | Under 5 MB | Tens of MB | Hundreds of MB | None (web) | None (web) | Hundreds of MB |

Where MDPrint differs: no install or account, works on locked-down machines, nothing leaves the browser, and PDFs keep selectable text.

Where the others are stronger: Typora offers WYSIWYG editing and more export formats; Obsidian has plugins, linking and a graph view for managing many notes; VS Code is a full editor with Git and debugging; StackEdit and Dillinger offer cloud sync.

## Limitations

- It is a single-document tool. There is no file library, linking or plugin system; use Obsidian or VS Code for that.
- Editing is source plus preview, not WYSIWYG like Typora.
- Export is PDF only.
- Only the Latin subsets of the bundled fonts are included; other scripts fall back to system fonts.
