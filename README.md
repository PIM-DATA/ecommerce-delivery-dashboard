# E-Commerce Delivery — Late Delivery Command Center 2026

Interactive dashboard analysing 50,000 e-commerce orders (Kaggle: `datascikhan/e-commerce-delivery-and-shipping-data-2026`) to find what drives late delivery.

**Open:** `dashboard/index.html` (works offline — all 50k rows are embedded; every chart cross-filters on click).

## Layout
- `data/` — source CSV from Kaggle
- `dashboard/template.html` — page source (HTML/CSS/JS)
- `dashboard/rows.json` — all orders encoded as base64 typed-array columns
- `dashboard/world.json` — world-atlas 110m TopoJSON (for the map)
- `dashboard/index.html` — built page (`template.html` + data injected)
- `dashboard/brief.html` — one-page executive / Marcom brief

## Rebuild
```bash
cd dashboard
python3 -c "t=open('template.html').read();d=open('rows.json').read();w=open('world.json').read();open('index.html','w').write(t.replace('__DATA__',d).replace('__WORLD__',w))"
```

## Key findings
- 56.3% of orders arrive after the promised date; 43% of those are only 1 day late.
- Weather (Snow 94% / Storm 91% vs Clear 35%), order priority (Low 82% — 26 h in warehouse vs 4.5 h for Urgent) and shipping method are the main drivers; carriers differ by ~18 pts at the same cost.
- A late order drops the customer rating from 4.2 to 2.7 and raises the return rate from 9% to 23%.
