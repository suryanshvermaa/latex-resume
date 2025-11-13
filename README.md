# 📄 Resume (LaTeX)

A clean, compact, and highly customizable resume built with LaTeX. The main source is `index.tex`, which compiles to `index.pdf` (A4).

## What’s inside 📦

- `index.tex` — LaTeX source for the resume
- `index.pdf` — generated after you compile (not tracked by default)
- `logo.png` — optional headshot/logo referenced in the header (you need to add this file yourself or disable the image block)

## Requirements 🧰

You’ll need a LaTeX distribution with the following packages commonly included:

- Base: `latexmk` (optional but recommended), `pdflatex`
- Packages: `geometry`, `xcolor`, `float`, `ragged2e`, `fullpage`, `wrapfig`, `tabularx`, `titlesec`, `marvosym`, `verbatim`, `enumitem`, `fancyhdr`, `multicol`, `graphicx`, `cfr-lm`, `fontenc` (T1), `fontawesome5`, `hyperref`, `microtype`, `array`, `setspace`, `tcolorbox`, `inputenc`, `latexsym`

### Quick install (Ubuntu/Debian) 🐧

- Minimal(ish) install:

```bash
sudo apt update
sudo apt install -y texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended texlive-fonts-extra latexmk
```

- Easiest (but large) install:

```bash
sudo apt update
sudo apt install -y texlive-full
```

> 💡 Note: `fontawesome5`, `tcolorbox`, and `cfr-lm` typically come with `texlive-latex-extra`/`texlive-fonts-extra`.

## Build 🛠️

From the project folder:

```bash
# Recommended (auto-runs as needed)
latexmk -pdf index.tex

# Or manual compile
pdflatex -interaction=nonstopmode -halt-on-error index.tex
pdflatex -interaction=nonstopmode -halt-on-error index.tex  # run twice for cross-refs
```

The output will be `index.pdf`.

### Clean build artifacts 🧹

```bash
# Clean aux/log files (keeps PDF)
latexmk -c

# Full clean (including PDF)
latexmk -C
```

## Customize 🎨

Most personal details are defined as macros near the top of `index.tex`:

```tex
% Personal Information
\newcommand{\name}{Suryansh Verma}
\newcommand{\course}{Bachelor of Technology}
\newcommand{\phone}{9580104753}
\newcommand{\emailb}{suryanshv.ug23.ee@nitp.ac.in}
\newcommand{\github}{suryanshvermaa}
\newcommand{\linkedin}{suryanshverma}
```

Update these to your own values. Sections are structured with small helper commands/macros:

- `\resumeSubheading{Title}{Right aligned}{Subtext (left)}{Right subtext}` for entries like education/experience
- `\resumeProject{Project Name}{Tech stack}{Date}{\href{...}{\faGithub}}` for project entries
- Use `\resumeItemListStart ... \resumeItemListEnd` to nest bullet points under entries
- Bullets use compact `\item[$\circ$]` style; you can change the default bullet appearance by editing `\labelitemi`/`\labelitemii` definitions in the preamble

### Header image (logo/photo) 🖼️

The header includes:

```tex
\includegraphics[width=1.8cm,clip]{logo.png}
```

- To use an image, add `logo.png` to the project root (recommended width ~1.8cm).
- To disable it, comment out the `\includegraphics` line or the entire left `\parbox`.

## Paper/formatting 📐

- Paper size: A4 (`a4paper,10pt` in the document class)
- Tight margins/spacing: tuned for a 1-page resume using `geometry`, `setspace`, `titlesec`, and compact list spacing
- Hyperlinks: colored dark blue via `hyperref`

## Troubleshooting 🧯

- Missing packages (e.g., `fontawesome5`, `tcolorbox`, `cfr-lm`):
  - Install `texlive-latex-extra` and `texlive-fonts-extra` or use `texlive-full`.
- `logo.png` missing error:
  - Add a `logo.png` file, or comment out the `\includegraphics{logo.png}` line.
- Weird bullets or list errors:
  - Ensure list items that use a circle label are written as `\item[$\circ$]` (math mode inside brackets).
- Overleaf:
  - Upload `index.tex` (and `logo.png` if used). Set compiler to pdfLaTeX. Paper size is A4 by default here.

## VS Code setup (optional) 🧩

Install the "LaTeX Workshop" extension for a great editing/preview experience. A simple setup is to use `latexmk`:

```jsonc
// .vscode/settings.json
{
  "latex-workshop.latex.tools": [
    {
      "name": "latexmk",
      "command": "latexmk",
      "args": ["-pdf", "-interaction=nonstopmode", "-halt-on-error", "%DOC%"]
    }
  ],
  "latex-workshop.latex.recipes": [
    { "name": "latexmk (pdf)", "tools": ["latexmk"] }
  ],
  "latex-workshop.view.pdf.viewer": "tab"
}
```

> 📝 You can also use `xelatex` if you prefer, but this template is tuned for pdfLaTeX and does not require XeLaTeX.

## License / Usage 📎

This template is intended for personal resume/CV use. Feel free to adapt the structure and styling, but replace personal details with your own before publishing.

---

If you run into issues compiling on Linux, share the error log (`index.log`) or the terminal output of `latexmk -pdf index.tex` so it can be diagnosed quickly.