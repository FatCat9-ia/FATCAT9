# Monthly Audience & Culture Intelligence — report template

Static page (no build step). The design lives in `index.html`; every month's content lives in `edition.json`.

## Structure

```
index.html            page, styles and rendering logic (do not edit monthly)
edition.json     the edition: findings, sheets, evidence, overview texts
fatcat9-logo.png
```

## Publish on GitHub Pages

1. Create a repository (private repos need a paid GitHub plan for Pages).
2. Upload these files keeping the same folders.
3. Settings → Pages → Source: "Deploy from a branch" → `main` / root.
4. The report is served at `https://<user>.github.io/<repo>/`.

## Monthly update

1. Copy `edition.json`, replace the content with the new edition.
2. Set `"synthetic": false` in `edition` to hide the sample banner.
3. Commit. Pages refreshes in a minute or two.

Tip: keep past editions as `data/2026-10.json`, `data/2026-11.json`, etc., and point
`index.html` (the `fetch('edition.json')` line) at the current one, or copy the
current edition to `edition.json` each month.

## Priority score

Computed by the page from `components` (each 0–100) and `scoring.weights`:
`score = Σ component × weight`. Change the weights or thresholds in `scoring` and
every chart and ranking updates automatically.

## Preview locally

`fetch` needs a local server: run `python3 -m http.server` in this folder and open
`http://localhost:8000`.
