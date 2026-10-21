# Mullah Tracker Roma

What a week in Rome costs: shared spending from Wed 14 Oct to Wed 21 Oct 2026, shown in both € and kr. Amounts can be typed in € or kr. (a switch on the amount field); kroner are converted at the fixed rate and stored as euro with four decimals.

- Live site (GitHub Pages): https://maraniras.github.io/mullahtracker/
- `index.html` is a static page that renders everything from `data.json`. There is no backend.
- The site is in Danish. Talk to the user in Danish.

## How it works

- `data.json`: `title`, `start`/`end` (Rome dates), `rate` (fixed DKK per EUR, 7.46) and `entries`: `{id, d, eur, t, ts}` = id, day (YYYY-MM-DD), amount in €, optional text, time of registration (ISO). One line per entry.
- Everyone can read the page. Editing is unlocked with "Rediger" in the footer: the user pastes a fine-grained GitHub token (only this repo, Contents: read and write). It is kept in that browser's `localStorage` only.
- When unlocked, the page reads and writes `data.json` through the GitHub contents API (one commit per added or deleted expense). It re-reads the file before every write, so two devices don't overwrite each other. Readers see changes once Pages has rebuilt (about a minute).
- Totals per day and for the whole period are computed on the page; nothing derived is stored.

## Files

- `index.html`: the page (Danish, mobile friendly, light/dark, Roman theme).
- `data.json`: settings and every expense.
- `.claude/serve.js`: tiny static server for local previews (port 8124).
