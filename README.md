# KPI Analyzer Dashboard

A single-file, zero-backend **traffic intelligence dashboard** for monitoring SEO and business KPIs. Built for IndiaMART's analytics team — load your data, explore trends, and share insights entirely in the browser.

![Dashboard Preview](https://img.shields.io/badge/status-live-10b981?style=flat-square) ![HTML](https://img.shields.io/badge/HTML-single--file-6366f1?style=flat-square) ![Chart.js](https://img.shields.io/badge/Chart.js-4.4.7-22d3ee?style=flat-square) ![No backend](https://img.shields.io/badge/backend-none-f59e0b?style=flat-square)

---

## Features

### Data Sources
| Source | Format | Metrics |
|--------|--------|---------|
| Google Search Console (GSC) | `.xlsx / .csv` | Clicks, Impressions, CTR, Avg Position |
| GA Daily — Overall | `.xlsx / .csv` | Users by page type (daily) |
| GA Daily — Organic | `.xlsx / .csv` | Organic users by page type |
| GA Daily — Internal | `.xlsx / .csv` | Internal navigation users |
| Business Metrics | `.xlsx / .csv` | Unique Senders, Requirements |

All data is processed **client-side** — nothing leaves the browser.

---

### Dashboard Tab

**KPI Summary Cards** — latest value, day-over-day delta badge, color-coded by metric.

**Daily Trend Chart** — multi-KPI line chart with:
- Canvas gradient area fills
- 7-day rolling average overlay (dashed line)
- Dual Y-axis for mixed-scale KPIs
- Smooth `easeInOutQuart` animations

**Data Summary Table** — scrollable matrix showing:
- Absolute values for last 14 / 30 / 60 days (or all)
- Δ previous day
- % vs 7-day average

**Day-over-Day Change Chart** — bar chart of DoD % for the primary KPI, last 14 days, green/red gradient bars.

**Last 7 Days Bar Comparison** — grouped bars for all active KPIs side by side.

**Same-Day Weekly Comparison** — pick any date and compare it against the same weekday across up to 26 prior weeks, with WoW change badges.

---

### Filters & Controls

| Control | Options |
|---------|---------|
| Date range | Custom from/to, or preset: 7D · 30D · 90D · 180D · All |
| Journey type | Overall · Organic · Internal |
| Page type | Overall · PDP · MCAT · Company · Home |
| Primary KPI | GSC: Impressions / Clicks / CTR / Position · GA: Users · Biz: Unique Senders / Requirements |
| Secondary–4th KPI | Same list, any combination |

---

### Notable Changes Tab

Log and track events that explain traffic anomalies:
- **Types**: Algorithm Update, Site Change, Campaign, Holiday, Bug, Other
- **Impact**: Positive / Negative / Neutral
- **Fields**: Date, description, affected KPIs, affected pages
- Persisted to `localStorage` — survives page refreshes
- Changes overlay on trend charts so spikes/drops have context

---

### Insights Tab

Auto-generated anomaly detection:
- Flags day-over-day drops or spikes **> 15%** across GSC and GA data
- Distinguishes **explained** (linked to a notable change) vs **unexplained** anomalies
- 30-day click trend summary vs prior 30 days
- 7-day average position trend
- Full sortable anomaly report table (top 50 shown)

---

## Quick Start

```bash
# No install needed — just open the file
open KPI_dashboard.html
```

1. Open `KPI_dashboard.html` in any modern browser (Chrome, Edge, Firefox).
2. Click **🧪 Demo** to load synthetic data and explore all features instantly.
3. Upload real `.xlsx` / `.csv` exports from GSC and GA to analyse live data.
4. Use the **Notable Changes** tab to annotate events, then switch to **Insights** for automated anomaly analysis.

---

## UI Design

| Element | Detail |
|---------|--------|
| Theme | Dark by default, full light-mode toggle |
| Topbar | Glassmorphism with `backdrop-filter: blur(20px)` |
| KPI cards | Gradient top-border per metric color, hover lift |
| Charts | Canvas `createLinearGradient` fills, rounded bars |
| Tooltips | Dark card, indigo border, `cornerRadius: 10` |
| Badges | Color-coded with subtle matching borders |
| Scrollbar | Custom 5px WebKit-styled |
| Animations | `easeInOutQuart`, 700–900ms, modal spring entrance |
| Fonts | Inter (UI) + JetBrains Mono (numeric values) |

---

## Dependencies (CDN — no install)

| Library | Version | Purpose |
|---------|---------|---------|
| [Chart.js](https://www.chartjs.org/) | 4.4.7 | All charts |
| [chartjs-plugin-annotation](https://www.chartjs.org/chartjs-plugin-annotation/) | 3.0.1 | Chart annotations |
| [SheetJS (xlsx)](https://sheetjs.com/) | 0.18.5 | Excel / CSV parsing |
| [Inter](https://fonts.google.com/specimen/Inter) | — | UI font |
| [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) | — | Monospace numbers |

---

## File Structure

```
KPI_Analyzer_Dashboard/
└── KPI_dashboard.html   # Complete self-contained app (HTML + CSS + JS)
```

Everything — styles, scripts, inline real data, and logic — lives in a single HTML file for easy sharing and zero-config deployment.

---

## Data Privacy

All file parsing and computation runs **entirely in the browser**. No data is sent to any server. The app works fully offline once loaded.

---

## License

Internal tool — IndiaMART Intermesh Ltd.
