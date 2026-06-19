# Part 4 — Tableau Executive Dashboard & Data Storytelling
**Analyst:** Aaditya Abhay Bogar (bitsom_ba_2511804)  
**Date:** 2026-06-19  
**Course:** Business Analytics — Data Visualization & Storytelling  

---

## Problem Statement

Design and build an executive-level Tableau dashboard that transforms transactional sales data into actionable business insights for senior leadership. The dashboard must go beyond descriptive summary to surface profit concentration risks, regional performance gaps, discount policy failures, and logistics inefficiencies — and present them through a structured narrative (data story) appropriate for C-suite consumption.

---

## Dataset

| Property | Value |
|---|---|
| File | `data/dashboard_sales_data.xlsx` |
| Records | 4,200 orders |
| Period | January 2024 – December 2025 |
| Regions | South, West, North, East |
| Categories | Technology, Furniture, Office Supplies |
| Sub-categories | 17 (Phones, Accessories, Copiers, Tables, Bookcases, etc.) |
| Customer Segments | Home Office, Corporate, Consumer |
| Ship Modes | Same Day, First Class, Second Class, Standard Class |
| Key Metrics | sales, profit, discount, quantity, return_flag, delivery_days |

---

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Tableau Desktop | Dashboard design, calculated fields, interactive filters |
| Python (pandas, numpy) | Pre-analysis and data validation |
| Python (matplotlib) | Dashboard screenshots and chart previews |
| Python (openpyxl) | Dataset inspection |

---

## Repository Structure

```
part4-tableau-dashboard/
├── data/
│   └── dashboard_sales_data.xlsx       # Source dataset (4,200 orders)
├── outputs/
│   ├── executive_dashboard.twbx        # Tableau packaged workbook
│   ├── full_dashboard.png              # Full dashboard screenshot
│   ├── sales_trend_view.png            # Worksheet 1: Monthly sales trend
│   ├── regional_performance_view.png   # Worksheet 2: Regional breakdown
│   ├── category_profitability_view.png # Worksheet 3: Category & sub-category
│   ├── filter_interaction_view.png     # Worksheet 4: Filter interaction demo
│   ├── business_insights.md            # 10 structured insights with evidence
│   ├── dashboard_story.md              # Executive narrative (leadership audience)
│   └── chart_selection_justification.md # Per-chart design rationale
└── README.md
```

---

## Steps Performed

### Step 1 — Data Exploration and Validation
Loaded `dashboard_sales_data.xlsx` into pandas for pre-analysis. Confirmed 4,200 records, 20 columns, no critical data quality issues. Validated that calculated fields (profit margin, return rate, avg order value) could be derived from available columns. Confirmed date range: Jan 2024–Dec 2025.

### Step 2 — Calculated Fields in Tableau
Created 7 custom calculated fields in the Tableau workbook:

| Calculated Field | Formula |
|---|---|
| Profit Margin | `SUM([profit]) / SUM([sales])` |
| Cost | `[sales] - [profit]` |
| Return Rate | `SUM([return_flag]) / COUNT([order_id])` |
| Avg Order Value | `SUM([sales]) / COUNTD([order_id])` |
| Shipping Delay Bucket | IF/ELSEIF on delivery_days |
| Profit per Order | `SUM([profit]) / COUNT([order_id])` |
| Discount Band | IF/ELSEIF on discount |

### Step 3 — Dashboard Design and Worksheet Creation
Built 7 worksheets in Tableau Desktop:
1. **Monthly Sales Trend** — Line chart of monthly sales, Jan 2024–Dec 2025
2. **Regional Performance** — Grouped bar: sales and profit by region
3. **Category Profitability** — Horizontal bar: profit by category with margin overlay
4. **Sub-Category Scatter** — Scatter plot: sales volume vs. margin, bubble = profit
5. **Discount Impact Analysis** — Bar chart: avg profit per order by discount band
6. **Shipping Mode Performance** — Dual-axis: order count + avg delivery days
7. **Return Rate by Category** — Bullet chart: return rate vs. company benchmark

Assembled all worksheets into a single executive dashboard layout with global filters (Region, Category, Date Range, Customer Segment) and interactive tooltips on all marks.

### Step 4 — Business Insight Extraction
Analyzed the dashboard views to extract 10 structured business insights. Each insight follows the format: Observation → Data Evidence → Business Interpretation → Recommended Action. Documented in `business_insights.md`.

### Step 5 — Dashboard Storytelling
Translated the 10 insights into a leadership narrative (`dashboard_story.md`) structured as a 5-chapter story: Executive Summary → Where We Are → The Opportunity → The Risk → The Actions. Written for a C-suite audience with no assumed technical background.

### Step 6 — Chart Justification Documentation
For each of the 7 charts, documented: the business question being answered, why the chosen chart type is optimal for that question, and the specific design principles applied. Documented in `chart_selection_justification.md`.

---

## Key Findings

### Financial Summary
- **Total Sales:** ₹217M | **Total Profit:** ₹33.3M | **Overall Margin:** 15.35%
- **Average Order Value:** ₹51,641 | **Average Discount:** 13.7%
- **Best Month:** August 2025 at ₹10.86M | **Worst Month:** April 2025 at ₹7.19M

### Regional Performance
| Region | Sales | Profit | Margin |
|---|---|---|---|
| South | ₹64.7M | ₹10.0M | 15.5% |
| West | ₹56.8M | ₹8.6M | 15.1% |
| North | ₹46.8M | ₹7.1M | 15.2% |
| East | ₹48.9M | ₹7.6M | 15.5% |

### Category Performance
| Category | Sales | Profit | Margin | Return Rate |
|---|---|---|---|---|
| Technology | ₹153.9M (70.9%) | ₹28.0M (84.2%) | 18.2% | 3.03% |
| Furniture | ₹51.6M (23.8%) | ₹3.4M (10.1%) | 6.9% | 7.67% |
| Office Supplies | ₹11.8M (5.4%) | ₹1.8M (5.6%) | 14.9% | 3.65% |

### Critical Discount Thresholds
| Discount Band | Avg Profit per Order |
|---|---|
| No Discount | ₹13,203 |
| 1–10% | ₹10,010 |
| 11–20% | ₹6,336 |
| 21–30% | ₹3,181 |
| 31–40% | **-₹1,601 (LOSS)** |

### Shipping Performance
| Ship Mode | Orders | % Share | Avg Delivery Days |
|---|---|---|---|
| Standard Class | 2,435 | 58.0% | 4.2 days |
| Second Class | 760 | 18.1% | 3.9 days |
| First Class | 682 | 16.2% | 2.9 days |
| Same Day | 323 | 7.7% | 0.3 days |

---

## The 10 Insights (Summary)

1. **Sales Trend:** Strong H2 2025 recovery — August (₹10.86M) highest month in dataset
2. **Regional:** South dominates (₹64.7M); East underperforms by ₹15.8M vs South
3. **Category Profitability:** Technology carries 84.2% of all profit at 18.2% margin
4. **Sub-Category:** Tables and Bookcases at 5.7% margin are the weakest performers
5. **Discount Impact:** Discounts 31–40% generate losses of -₹1,601/order
6. **Shipping:** Standard Class (58% of orders) averages 4.2 days — a customer experience risk
7. **Returns:** Furniture return rate (7.67%) is 2.5× Technology (3.03%)
8. **Business Risk:** 13.7% avg discount + 15.35% margin = thin structural buffer
9. **Customer Segment:** Home Office leads at ₹74.5M; all segments similarly margined (~15.3%)
10. **Channel:** Organic drives 40% of orders; Paid channel needs ROI analysis

---

## Deliverable Files

| File | Description |
|---|---|
| `executive_dashboard.twbx` | Tableau packaged workbook with embedded data |
| `full_dashboard.png` | Screenshot of complete dashboard layout |
| `sales_trend_view.png` | Monthly sales trend chart view |
| `regional_performance_view.png` | Regional breakdown chart view |
| `category_profitability_view.png` | Category and sub-category profitability view |
| `filter_interaction_view.png` | Dashboard filters and interaction demo |
| `business_insights.md` | 10 structured insights with data evidence |
| `dashboard_story.md` | Executive narrative for leadership audience |
| `chart_selection_justification.md` | Chart type and design principle rationale |

---

## Assumptions and Limitations

1. **Margin calculations** use recorded sales and profit from the dataset. Known sales/profit calculation mismatches (from Part 1 cleaning) exist in this dataset but are not corrected at this stage — the dashboard reflects the source data as provided.
2. **Tableau packaged workbook** (`.twbx`) is a ZIP archive containing the Tableau workbook XML and the embedded data extract. Open with Tableau Desktop 2021.4+ or Tableau Reader (free).
3. **Campaign spend data not available** — the channel split (Organic, Paid, Email, Referral) shows order volume by channel but cannot show ROI without corresponding marketing cost data.
4. **Return rate is binary** — return_flag is 0/1; partial returns and exchanges are not captured separately in this dataset.
5. **Sub-category cost structure** — the recommendation to audit Tables and Bookcases assumes that fully-loaded costs (including reverse logistics) would further reduce their margins. This cannot be confirmed from the current dataset alone.

---

## How to Open the Dashboard

1. Install **Tableau Desktop** (any version 2021.4+) or **Tableau Reader** (free download from tableau.com)
2. Double-click `executive_dashboard.twbx` — Tableau will open the packaged workbook with the embedded data automatically
3. Use the **Region**, **Category**, **Date Range**, and **Segment** filters in the top-right to drill into specific views
4. Hover over any mark for detailed tooltips showing the exact figures behind each data point
