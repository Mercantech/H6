# H6

Skabelon til MAGS svendeprøven. Overblik og krav: [H6 på Mercantec](https://mercantec.notion.site/h6).

## Kildekode (`src/`)

Al **kode**, der hører til produktet (applikation, scripts, tests), bør ligge under **`src/`**, så roden af repoet primært kan rumme dokumentation, konfiguration og værktøjer — fx `Rapport/` til MkDocs. Opret undermapper efter behov (fx `src/api/`, `src/lib/`). Se [`src/README.md`](src/README.md) for den korte vejledning.

## Notes

Valgfri Obsidian-noter. Vil I ikke bruge dem, så slet mappen `Notes` (og evt. `.obsidian`).

## Dokumentation (MkDocs)

Skriv i Markdown under [`Rapport/docs/`](Rapport/docs/). Preview:

```bash
cd Rapport
pip install -r requirements-docs.txt
mkdocs serve
```

Åbn [http://127.0.0.1:8000](http://127.0.0.1:8000).

**Docker** (samme mappe som `Dockerfile`):

```bash
cd Rapport
docker build -t h6-rapport .
docker run --rm -p 8000:8000 h6-rapport
```

PDF-export: `npm install` og `npm run pdf` i `Rapport` (kræver kørende docs-URL; se `Rapport/scripts/export-print-pdf.mjs`).
