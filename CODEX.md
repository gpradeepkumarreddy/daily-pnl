# Trading P&L Calendar – Notes & Ideas

## Project snapshot
- **Views**: `index.html` (CSV-driven calendar), `index_tos.html` (TOS statement parser demo).
- **Data**: `trades.csv` with `date,pnl` rows; `2026-02-06-AccountStatement.csv` sample statement.
- **Layout**: Dark, modern calendar heatmap with monthly metrics and a YTD strip. Sunday-start week. Month nav via Prev/Next buttons. YTD metrics compute across all CSV rows.

## How it works
- **Calendar**: Builds grid for the selected month, coloring cells by P&L magnitude. Metrics: running total, highest day, lowest day, win rate.
- **Month navigation**: Prev/Next cycles through months detected in `trades.csv`.
- **YTD metrics**: Running total, average daily P&L, win rate, longest win/loss streak (weekday gaps reset streaks; weekends ignored). Colored for positive/negative/neutral.
- **TOS page**: Parses statement CSV to derive daily P&L from start/end balances; includes file-upload fallback.

## Current gaps / future improvements
- **Data ingestion**
  - Add month picker + inline CSV upload in main view with validation/toast feedback.
  - Allow manual quick-entry for a single day and append to `trades.csv`.
  - Direct TOS statement import into `index.html` (reuse parser from `index_tos.html`).
- **Insights**
  - Add monthly cumulative P&L sparkline and daily-return histogram.
  - “Compare to prior month” deltas and highlighting.
  - Notes per day (sidecar JSON), shown on hover.
- **UX polish**
  - Hover tooltips with P&L, month-to-date total, and note (if any).
  - Smooth month transitions (slide/fade) and subtle background gridlines.
  - Toggle to hide zero/empty days or highlight losses only.
  - Skeleton/loading state while CSV fetches.
- **Export/Share**
  - One-click PNG export of the calendar + metrics.
  - Download filtered month as CSV.
- **Performance/Robustness**
  - Lazy-render months on demand for large histories.
  - Graceful handling of malformed CSV rows with inline errors.
  - Option to group by year and show a multi-month overview.

## Quick commands
- Serve locally: `python3 -m http.server 8000` (then visit `http://localhost:8000/`).
- Git status: `git status`.
