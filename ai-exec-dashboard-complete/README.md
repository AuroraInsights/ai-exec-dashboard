
# AI Executive Dashboard — Complete Prototype

A runnable Streamlit dashboard with validation gates, executive scorecards, trends, leaderboards, an editable Executive Brief, and export to PDF/PPT.

## Run locally
```bash
pip install -r requirements.txt
streamlit run app/app.py
```
Data loads from `./data/*.csv` by default (12 months of synthetic data included).

## Validations (gate before render)
- Not-null & ranges on key fields
- Month must be first-of-month
- Freshness: latest month within 45 days across KPI tables
- Reconciliation: latest `kpi_funding.total_usd` ≈ `SUM(deals_n.amount_usd)` ±3%
- Outlier flags: MoM change > 30% for Funding, ICI, and Job postings

If validations fail, the app displays a red banner and keeps running so you can inspect data.

## Exports
- **PDF:** 1–2 pages with the Executive Brief and a metrics summary
- **PPTX:** Single slide with the edited brief (ready to drop into a board deck)

## Next steps
- Swap synthetic CSVs for your warehouse views
- Expand validation with Great Expectations or dbt tests
- Add sector spotlight and evidence tooltips per KPI tile
