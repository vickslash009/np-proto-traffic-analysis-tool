# NP Proto Traffic Analysis Tool

A single-page SEO dashboard that explains where organic traffic moved, which sections, URLs and keywords caused it, why it likely happened, and what to do next.

## What it does

- **Views:** Overview, Sections, Pages, Keywords, a page drill-down and a keyword drill-down.
- **Global filters:** date range with GA4/GSC-style comparisons, section, device, country, brand or non-brand, and page type.
- **Trend charts:** Daily, Weekly and Monthly grouping, metric toggles, a dotted comparison overlay and hover tooltips.
- **Every URL listed:** tables are paginated, searchable, sortable and export to CSV.
- **Plain-language reasons:** every finding is written as what happened, why it likely happened (with evidence and a Likely or Possible label) and what to do.
- **Project selector:** lists your Search Console properties and loads one at a time. This needs the SearchConsole.ai MCP server and the Claude desktop app.
- **Evidence sources:** Search Console for traffic, SEMrush for AI Overview, volume and competitor data, and a crawl plus URL Inspection for index checks.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app: styles, scripts and the built-in demo data |
| `data/project.json` | Prebuilt project data and its settings. Not committed; see below |

## Running it

The page is published as a Claude Artifact, which adds the HTML document wrapper at publish time. To open it locally, serve the folder:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.

Without a `data/` file, the dashboard shows a clearly labelled demo client. You can also load your own CSV exports under **Setup**.

## Client data

Client data is excluded by `.gitignore` because it contains real Search Console, SEMrush and crawl results. When a `data/project.json` file is present locally, the dashboard opens that project by default. Project-specific settings such as brand terms and page types live in that file, not in the code.

## Known limits

- URL and keyword detail covers the latest 56 days. Site totals cover 16 months.
- Query-level rows come from the top of the Search Console export, so very small keywords can look new or lost when they only crossed the cutoff.
- Lost-link checks need Ahrefs data, and Google update checks need update dates entered in **Setup**.
- Weekly email or Slack alerts are not built yet.
