# Markdown → PDF Studio (MarkPrint)

A zero-dependency, self-contained Markdown editor and live preview tool designed for exporting high-fidelity, vector-crisp PDF documents using the browser's native print rasterizer.

**No build step. No npm. No server.** Just double-click `index.html` to run in any modern web browser.

---

## ✨ Features

- **Two-Pane Workspace**:
  - Left pane: Raw Markdown editor with monospace typography, 2-space tab indentation, and quick formatting shortcuts.
  - Right pane: Live preview sheet styled like a clean desktop publication.
  - Interactive Splitter: Draggable divider to adjust pane widths (double-click to reset 50/50).
  - Responsive: Automatically stacks vertically on screens $\le 768\text{px}$.

- **GitHub Flavored Markdown (GFM)**:
  - Formatted tables with zebra-striping and bold headers.
  - Task lists with custom interactive checkboxes (no bullet artifacts).
  - Strikethrough (`~~text~~`), autolinks, blockquotes, and headings.

- **Advanced Document Add-ons**:
  - **Code Syntax Highlighting**: Powered by `highlight.js` with language detection, language badges, and a 1-click "Copy" code button.
  - **KaTeX Mathematical Notation**: Renders inline formulas (`$E = mc^2$`) and display equation blocks (`$$\dots$$`).
  - **Mermaid.js Vector Diagrams**: Renders interactive, infinite-resolution SVGs for ````mermaid flowcharts, sequence diagrams, and class graphs.

- **Native Vector PDF Export (Browser Print Engine)**:
  - Generates crisp, selectable, searchable PDFs without blurry rasterization (`html2canvas` and `jsPDF` are not used).
  - Strict print stylesheet rules:
    - `@page { margin: 18mm }`
    - Automatically hides headers, toolbars, buttons, editor pane, and scrollbars.
    - Prevents orphaned headings: `h1, h2, h3, h4, h5, h6 { break-after: avoid; }`
    - Prevents page breaks inside blocks: `pre, table, img, blockquote, .mermaid-wrapper, .katex-display, tr { break-inside: avoid; }`
    - Wraps long code lines (`white-space: pre-wrap; word-break: break-word;`) so code never clips off the page.
    - Constrains images to `max-width: 100%`.
    - Converts hyperlinks to inherited-color plain text (no bright blue underlines).

- **Theme & Persistence**:
  - **Dark Mode**: High-contrast slate dark theme that also syncs with the print output.
  - **LocalStorage Auto-Save**: Automatically preserves your draft, active filename, theme, and splitter position across browser reloads.
  - **File Reader & Drag-and-Drop**: Load `.md` or `.txt` files with the "Open .md" button or by dragging files directly into the browser window.
  - **Copy HTML**: 1-click button to copy the rendered HTML directly to the clipboard.
  - **Document Statistics**: Real-time word count, character count, and reading time estimation.

---

## 🚀 Quick Start

1. Double-click `index.html` to open it in Google Chrome, Microsoft Edge, Mozilla Firefox, or Safari.
2. Edit or paste Markdown into the left editor pane.
3. Click **"Export PDF"** (or press <kbd>Ctrl+P</kbd> / <kbd>Cmd+P</kbd>).

---

## 🖨️ PDF Export Tips

When the browser print dialog opens:
- **Destination**: Choose *"Save as PDF"*.
- **Margins**: Set to *"Default"* (the stylesheet already configures precise `18mm` margins).
- **Background Graphics**: Ensure *"Background graphics"* is **checked** if you want code block backgrounds, table shading, or dark mode background colors to appear in the PDF.
- **Headers and Footers**: Uncheck if you prefer a clean document without browser date/URL stamps.

---

## ⌨️ Shortcuts & Formatting Helpers

| Shortcut / Action | Description |
| :--- | :--- |
| <kbd>Tab</kbd> | Indent line(s) by 2 spaces |
| <kbd>Shift</kbd> + <kbd>Tab</kbd> | Dedent line(s) by 2 spaces |
| <kbd>Ctrl</kbd> / <kbd>Cmd</kbd> + <kbd>P</kbd> | Open print / PDF export dialog |
| Double-click Splitter | Reset editor and preview to 50/50 split |
| **Sample Button** | Replaces current draft with a comprehensive feature showcase |

---

## 📁 Project Structure

```
md preview tool/
├── index.html     # Single self-contained HTML application
└── README.md      # Documentation and usage guide
```

---

## 📊 How MarkPrint Compares

| Feature | **MarkPrint** | Typora ($15) | Obsidian (Free) | StackEdit | Dillinger | VS Code + Extension |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Setup Required** | ❌ None — just open HTML | Install app | Install app + plugins | Create account | Open website | Install editor + extensions |
| **Works Offline** | ✅ Yes (after first load) | ✅ Yes | ✅ Yes | ❌ No | ❌ No | ✅ Yes |
| **PDF Export Quality** | ✅ Vector (native print) | ✅ Vector | ⚠️ Plugin-dependent | ⚠️ Rasterized | ⚠️ Basic | ⚠️ Plugin-dependent |
| **Selectable Text in PDF** | ✅ 100% | ✅ Yes | ⚠️ Varies | ❌ No | ❌ No | ⚠️ Varies |
| **Math (LaTeX/KaTeX)** | ✅ Built-in | ✅ Built-in | ⚠️ Plugin | ✅ Built-in | ❌ No | ⚠️ Plugin |
| **Mermaid Diagrams** | ✅ Built-in | ⚠️ Plugin | ⚠️ Plugin | ❌ No | ❌ No | ⚠️ Plugin |
| **Code Syntax Highlighting** | ✅ 190+ languages | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Dark Mode** | ✅ Yes (syncs to PDF) | ✅ Yes | ✅ Yes | ❌ No | ❌ No | ✅ Yes |
| **Live Preview** | ✅ Real-time | ✅ WYSIWYG | ✅ Real-time | ✅ Real-time | ✅ Real-time | ✅ Real-time |
| **Portable (single file)** | ✅ 1 HTML file | ❌ No | ❌ No | ❌ No | ❌ No | ❌ No |
| **Data Privacy** | ✅ 100% local | ✅ Local | ✅ Local | ❌ Cloud-stored | ❌ Cloud-stored | ✅ Local |
| **Cost** | **Free** | $14.99 | Free (core) | Free (limited) | Free | Free |
| **File Size** | ~60 KB | ~80 MB | ~300 MB | N/A (web) | N/A (web) | ~300 MB + plugins |

### Where MarkPrint Wins

- **Zero friction**: No install, no account, no build step. Download one file → double-click → you're working. Share it via email, USB stick, or Slack and the recipient can use it immediately.
- **Superior PDF output**: The browser's native print engine produces vector-quality PDFs with fully selectable, searchable text. Tools using `html2canvas` or `jsPDF` rasterize text into blurry pixels.
- **Air-gapped / restricted environments**: Works on machines where you can't install software — government networks, corporate lockdown PCs, shared lab computers. Just drop the HTML file and open it.
- **True portability**: Your entire editor + renderer + preview + PDF exporter fits in a single ~60 KB file. No dependency on a cloud service that could shut down, change pricing, or hold your data hostage.
- **Math + Diagrams + Code in one tool**: KaTeX, Mermaid.js, and Highlight.js are all built-in. No hunting for plugins, no compatibility issues, no configuration.

### Where Others Win (honest trade-offs)

- **Typora** offers true WYSIWYG editing (no split panes), more export formats (DOCX, EPUB, LaTeX), and custom CSS themes.
- **Obsidian** has a massive plugin ecosystem, bi-directional linking, graph view, and is built for long-term knowledge management — not just single-document editing.
- **VS Code** is a full IDE with Git integration, terminal, debugging, and thousands of extensions — MarkPrint is intentionally simpler.
- **StackEdit / Dillinger** offer real-time collaboration and cloud sync — MarkPrint is local-only by design.

---

## 🛠️ Dependencies

Loaded directly via CDN (no installation or bundler required):
- [Marked.js](https://marked.js.org/) — Fast Markdown and GFM parser
- [Highlight.js](https://highlightjs.org/) — Syntax highlighting for code blocks
- [KaTeX](https://katex.org/) — Math formula typesetting
- [marked-katex-extension](https://github.com/markedjs/marked-katex-extension) — KaTeX integration for Marked
- [Mermaid.js](https://mermaid.js.org/) — Vector diagram rendering

