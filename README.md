# Factions Wiki

MkDocs documentation site for MassiveCore plugins (Factions, FactionsChat, CreativeGates, and related plugins). Live site: [https://factions.wiki/](https://factions.wiki/).

## Prerequisites

- [Python](https://www.python.org/downloads/) 3.9+ (3.13 works)
- `pip`

## Setup

From the project root:

```bash
python -m venv .venv
```

Activate the virtual environment:

- **Windows (PowerShell):** `.\.venv\Scripts\Activate.ps1`
- **Windows (cmd):** `.\.venv\Scripts\activate.bat`
- **macOS / Linux:** `source .venv/bin/activate`

Install dependencies:

```bash
pip install -r requirements.txt
```

(`mkdocs-material` pulls in MkDocs and the Markdown extensions used by this site.)

## Run locally (live preview)

```bash
mkdocs serve
```

Then open [http://127.0.0.1:8000/](http://127.0.0.1:8000/). The server reloads when you edit files under `docs/` or `mkdocs.yml`.

Useful options:

```bash
mkdocs serve -a 0.0.0.0:8000   # listen on all interfaces
mkdocs serve --dirty           # faster rebuilds (changed pages only)
```

## Build (compile) the static site

```bash
mkdocs build
```

Output goes to the `site/` directory (already gitignored). For a clean rebuild:

```bash
mkdocs build --clean
```

To preview the built site without the live-reload server:

```bash
mkdocs build
python -m http.server -d site 8000
```

## Project layout

| Path | Purpose |
|------|---------|
| `mkdocs.yml` | Site config, nav, theme (Material) |
| `docs/` | Markdown source pages and static assets |
| `site/` | Generated HTML (from `mkdocs build`) |
| `requirements.txt` | Python dependencies |

## Deploy note

Production is served from the built `site/` output (or your host’s MkDocs / static-site pipeline). Building locally is enough to verify changes before publish.
