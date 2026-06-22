# SuperStore Sales Dashboard — Power BI

A two-page Power BI dashboard built on 22K+ retail orders from a US superstore (2019–2021). Page 1 breaks down $1.57M in sales across regions, segments, categories, and payment methods. Page 2 runs a 15-day sales forecast with a state-level breakdown.

Live on Power BI Service → [View Report](https://app.powerbi.com/groups/me/reports/909a1cf6-4c85-484c-a24d-e718a4d98839)

---

## What's Inside

**Page 1 — Sales Overview**

- KPI cards: 22K orders, $1.57M sales, $175K profit, 3.93 avg ship days
- Sales by month (area chart, 2019–2021 layered)
- Profit by month (line chart — Q4 spikes every year without fail)
- Donut charts: payment mode, customer segment, region
- Sales by ship mode and product category
- Bar chart: top sub-categories (Phones at $0.20M, Chairs close behind)
- ArcGIS map: profit and sales plotted by state

**Page 2 — Forecast**

- 15-day sales forecast with confidence bands (Power BI built-in analytics)
- Zoom slider for Oct 2020–Jan 2021 closeup
- Bar chart: top 10 states by sales (California at $0.34M, nearly 2x New York)

---

## Dataset

`SuperStore_Sales_Dataset.csv` — 9,800 rows, 23 columns

| Field | Description |
|---|---|
| Order Date / Ship Date | Used to calculate ship days and monthly trends |
| Segment | Consumer (48%), Corporate (33%), Home Office (19%) |
| Category | Furniture, Technology, Office Supplies |
| Sales / Profit | Core metrics |
| Payment Mode | COD, Online, Cards |
| Region | Central, East, South, West |
| State | 49 US states |

Date range: Jan 2019 – Dec 2020 (forecast extends to Jan 2021)

---

## Key Findings

- **Standard Class ships 60% of orders** but Same Day is only 2% — customers are clearly trading speed for cost
- **California alone is 22% of total sales** — the West region punches well above its geographic size
- **Office Supplies leads in volume ($0.64M) but Furniture has the weakest profit margins** — a real ops problem if this were a live business
- **Q4 spikes consistently** — November and December carry a disproportionate share of both sales and profit every year

---

## Tools Used

- Power BI Desktop (data model, DAX, report design)
- Power BI Service (publish, share)
- DAX measures: `Total Sales`, `Total Profit`, `Avg Ship Days`, `Orders Count`
- Power BI Analytics pane for forecast (15-day, 95% confidence)
- ArcGIS Maps visual for geographic layer

---

## DAX Snippets

```dax
-- Average shipping time
Avg Ship Days = AVERAGEX(Orders, Orders[Ship Date] - Orders[Order Date])

-- Profit margin
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)

-- YOY Sales Growth
YOY Growth = 
DIVIDE(
    [Total Sales] - CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Calendar'[Date])),
    CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Calendar'[Date]))
)
` ` `
---

## Dashboard Screenshots

**Page 1 — Sales Overview**
![Sales Overview] <img width="1587" height="887" alt="Screenshot 2026-06-22 at 12 38 19 PM" src="https://github.com/user-attachments/assets/8d4d46f3-d207-450f-9f75-7b0eaf5caaf5" />

**Page 2 — Forecast**
![Forecast] <img width="1587" height="887" alt="Screenshot 2026-06-22 at 12 38 55 PM" src="https://github.com/user-attachments/assets/6ebbb17a-460f-435c-9299-f0900ffd3290" />

---

## How to Run Locally

1. Download `Superstore_Sales_Dashboard.pbix`
2. Open in Power BI Desktop (free)
3. If prompted to refresh, point it to `SuperStore_Sales_Dataset.csv` in the same folder
4. All visuals and measures reload automatically

No credentials. No gateway. Just the two files.

---

**Aishwarya Kadam**
[LinkedIn](https://linkedin.com/in/aish0830) · [GitHub](https://github.com/Aishwaryakadam-30)


