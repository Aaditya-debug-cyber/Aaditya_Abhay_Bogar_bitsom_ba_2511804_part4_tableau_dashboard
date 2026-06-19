# Chart Selection Justification — Executive Dashboard
**Analyst:** Aaditya Abhay Bogar (bitsom_ba_2511804)  
**Date:** 2026-06-19  
**Dashboard:** Executive Sales & Profitability Dashboard (Tableau)

---

## Overview

The executive dashboard contains 7 worksheets, each answering a specific business question. This document explains: (1) the business question each chart addresses, (2) why the chosen chart type is appropriate, and (3) the design principles applied to maximize clarity for a leadership audience.

---

## Chart 1 — Monthly Sales Trend (Line Chart)

**Business Question:** How have sales evolved month-over-month over the 24-month period? Are there seasonal patterns, and is the business growing or declining?

**Chart Type: Line Chart**

A line chart is the canonical choice for time-series data because it:
- Encodes time on the x-axis in a natural left-to-right reading direction
- Uses position along a common scale (y-axis) to encode magnitude — the most accurate pre-attentive attribute for quantitative comparison
- Makes trend direction (slope) immediately visible without requiring the viewer to compare individual bar heights
- Allows easy identification of peaks, troughs, and inflection points

A bar chart would be a reasonable alternative for monthly comparison, but it would emphasize individual month comparison over trend — which is the wrong emphasis when the primary question is about trajectory. A scatter plot would lose the time-ordering signal.

**Design Principles Applied:**
- **Data-ink ratio:** No gridlines behind the line; only horizontal reference lines at meaningful thresholds (average monthly sales)
- **Annotation:** Key peaks (July ₹10.66M, August ₹10.86M) and key trough (April ₹7.19M) annotated directly on the chart so the viewer does not have to cross-reference a table
- **Color:** Single line in a distinct color (blue) against a white background — no color encoding needed because only one measure is displayed
- **Axis:** Y-axis starts at a non-zero baseline but includes a clear break indicator to avoid misleading compression of the trend magnitude

---

## Chart 2 — Regional Sales & Profit Bar Chart (Grouped Bar)

**Business Question:** Which regions generate the most sales and profit? Is the regional profit distribution proportional to sales, or do some regions punch above or below their weight?

**Chart Type: Grouped Bar Chart (Sales + Profit per Region)**

A grouped bar chart is appropriate here because:
- There are only 4 regions — a small discrete number of categories well-suited to bars
- Two related measures (sales and profit) are displayed side-by-side to allow within-region and across-region comparison simultaneously
- Bar length encodes magnitude on a common zero baseline — the most accurate perceptual encoding for comparing absolute values across categories
- The grouping makes it immediately visible whether a region's profit bar is proportionally shorter than its sales bar (indicating lower margin)

A stacked bar would be acceptable for showing composition, but it makes it harder to compare the profit bars across regions. A map would show geographic distribution but would lose the precise magnitude comparison.

**Design Principles Applied:**
- **Color coding:** Sales bars in blue, profit bars in orange — consistent color convention used throughout the dashboard for these two measures
- **Sorting:** Regions sorted by sales descending (South, West, North, East) to immediately surface the performance ranking
- **Labels:** Absolute values labeled on bar tops for precision; the visual height provides the relative comparison
- **No 3D effects:** Flat 2D bars only — 3D bars distort perceptual area judgments and add no information

---

## Chart 3 — Category Profitability (Horizontal Bar Chart with Margin Overlay)

**Business Question:** Which product categories generate the most profit, and how does margin vary across categories? Is the business's profit concentration a risk?

**Chart Type: Horizontal Bar Chart with Margin Percentage Labels**

Horizontal bars are chosen over vertical bars because:
- Category names (Technology, Furniture, Office Supplies) are longer text labels — horizontal bars allow them to be read naturally on the y-axis without rotation
- The question is about ranking and comparing magnitudes across a small set of categories, which horizontal bars support well
- A pie chart would show share of total but would make it impossible to see absolute profit amounts or margin rates — both of which are critical to this insight

The margin percentage is overlaid as a text annotation rather than a second axis to avoid dual-axis confusion.

**Design Principles Applied:**
- **Diverging color saturation:** Higher-margin categories use a more saturated color; lower-margin categories use a lighter shade — this pre-attentively signals quality, not just quantity
- **Margin callout:** The 18.2% (Technology), 14.9% (Office Supplies), 6.9% (Furniture) margin figures are displayed directly on the chart — the viewer can answer both "how much profit?" and "how efficiently?" in a single look
- **Reference line:** A vertical reference line at the company-wide 15.35% margin is included to show which categories beat or miss the average

---

## Chart 4 — Sub-Category Profit Margin Scatter Plot

**Business Question:** Within the product portfolio, which specific sub-categories are profit contributors and which are margin drags? Is there a relationship between sales volume and margin?

**Chart Type: Scatter Plot (Sales on X-axis, Profit Margin on Y-axis, bubble size = absolute profit)**

A scatter plot is the only chart type that simultaneously encodes three quantitative variables:
- X-axis (sales volume): How big is this sub-category in revenue terms?
- Y-axis (profit margin): How efficiently does it generate profit?
- Bubble size (absolute profit): What is the total profit contribution?

This allows a leadership audience to immediately see four quadrants: high volume / high margin (ideal), high volume / low margin (scale-up opportunity), low volume / high margin (niche stars), and low volume / low margin (portfolio candidates for review).

A bar chart could show margin by sub-category, but it would lose the volume and absolute profit dimensions. A heat map would require more cognitive effort to interpret three variables simultaneously.

**Design Principles Applied:**
- **Quadrant lines:** Reference lines at the median sales and at the 15.35% average margin divide the chart into four labeled quadrants — this structures the insight without requiring the viewer to do mental categorization
- **Color by category:** Technology sub-categories in blue, Furniture in orange, Office Supplies in green — consistent with the category color scheme
- **Labeling:** Only the extreme outliers (Tables, Bookcases at bottom-left; Copiers, Phones at top-right) are labeled directly. Other sub-categories are labeled on hover in the interactive Tableau version to avoid clutter
- **Bubble scaling:** Bubble area (not radius) is proportional to profit — using radius would overstate differences

---

## Chart 5 — Discount Band vs. Average Profit per Order (Bar Chart with Reference Line)

**Business Question:** What is the relationship between discount level and profitability? At what discount threshold does a transaction become loss-making?

**Chart Type: Bar Chart (Discount Band on X-axis, Avg Profit per Order on Y-axis)**

A bar chart with a zero reference line is the clearest way to show this because:
- The discrete discount bands (No Discount, 1-10%, 11-20%, 21-30%, 31-40%) are categorical — not continuous — making bars more appropriate than a line
- Bars crossing below the zero line are immediately visible as losses — this is the key insight and the chart type makes it impossible to miss
- A line chart would imply continuity between the bands and would make the below-zero crossing harder to see as a discrete threshold

**Design Principles Applied:**
- **Color:** Bars above zero are green; bars below zero are red — color pre-attentively signals the profit/loss boundary without requiring the viewer to read the y-axis
- **Zero reference line:** Bold horizontal line at y=0 is the most important element in the chart — it is styled to be visually prominent
- **Value labels:** Average profit per order is labeled on each bar (e.g., -₹1,601 for the 31-40% band) so the viewer gets both the direction and the magnitude
- **Title framing:** Chart title is "Discounts Above 30% Destroy Value" — a declarative title that tells the viewer the conclusion, allowing them to use the chart to verify rather than to discover

---

## Chart 6 — Shipping Mode Distribution and Delivery Performance (Combined Bar + Dot Plot)

**Business Question:** How are orders distributed across shipping modes, and does the delivery time meet expectations? Is Standard Class a customer experience risk?

**Chart Type: Bar Chart (order volume) + Dot Plot (avg delivery days) on dual axis**

This combination is used because:
- Order volume (how many orders per shipping mode) and average delivery days (how fast) are related but different measures — displaying them together avoids requiring the viewer to mentally join two separate charts
- Bars show volume (discrete count), dots show a rate/average (continuous measure) — mixing chart types signals to the viewer that these are different kinds of measures
- A pure bar chart showing only counts would miss the delivery performance signal entirely

**Design Principles Applied:**
- **Dual axis with clear labeling:** Left y-axis (bars) = order count; right y-axis (dots) = average delivery days. Both axes are clearly labeled with units to prevent misreading
- **Color consistency:** Bars in blue (order volume); dots in orange (delivery days) — orange signals a warning/time metric throughout the dashboard
- **Annotation:** The 4.2-day average for Standard Class is annotated with a callout box because it is the headline risk metric for this chart
- **Sorting:** Shipping modes sorted by order volume descending so the most impactful mode (Standard Class) appears first

---

## Chart 7 — Return Rate by Category (Bullet Chart / Gauge)

**Business Question:** Which categories have the highest return rates, and how does each compare to the company average?

**Chart Type: Bullet Chart (actual return rate vs. company average benchmark)**

A bullet chart is chosen over a simple bar chart or gauge because:
- It shows both the actual value (return rate) and a comparison benchmark (company average return rate) in the same visual space
- It is more space-efficient than a gauge, allowing all three categories to be compared on a single visual
- It avoids the visual distortion of circular gauge charts, which use angle to encode magnitude — a less accurate perceptual encoding than position on a common scale

**Design Principles Applied:**
- **Benchmark line:** The company-wide average return rate (4.78%) is marked as a vertical reference line within each bullet bar — Furniture (7.67%) is immediately visible as an outlier above the benchmark
- **Color bands:** Background shading in three bands (acceptable range, warning range, critical range) provides context for whether a return rate is normal or problematic without requiring external benchmarks
- **Direct labeling:** Percentage return rates labeled directly to the right of each bar — no legend required
- **Consistent scale:** All three category bullets share the same x-axis scale (0% to 10%) to allow direct comparison

---

## Summary Table

| Chart | Type | Primary Question | Key Design Choice |
|---|---|---|---|
| Monthly Sales Trend | Line Chart | Trend over time | Annotated peaks/troughs |
| Regional Performance | Grouped Bar | Which region leads? | Sales + profit side-by-side |
| Category Profitability | Horizontal Bar | Category margin comparison | Margin % overlay |
| Sub-Category Scatter | Scatter (bubble) | Volume vs. margin vs. profit | 3-variable encoding in one view |
| Discount Impact | Bar + zero line | Where do discounts become losses? | Red/green color above/below zero |
| Shipping Performance | Bar + dot (dual axis) | Volume vs. speed by mode | Dual axis for different measure types |
| Return Rate | Bullet Chart | Return rate vs. benchmark | Benchmark line within each bar |

---

## General Design Principles Consistently Applied Across All Charts

**1. Declarative titles:** Every chart title states a finding ("Discounts Above 30% Destroy Value"), not a description ("Discount Band Analysis"). This respects the viewer's time and signals the key takeaway immediately.

**2. Minimal gridlines:** Only horizontal gridlines where they aid reading. No decorative borders, shadows, or background colors that add visual noise without information.

**3. Consistent color convention:** Blue = sales volume / positive metrics; Orange = time/delivery/warning; Green = profit above threshold; Red = loss/below threshold. This convention is established in the first chart and maintained throughout.

**4. Direct labeling over legends:** Where possible, data labels are placed directly on or next to the data mark. Legends require the viewer to look back and forth; direct labels eliminate that cognitive step.

**5. Sorting by relevance, not alphabetically:** Categories and regions are sorted by the measure being analyzed (usually descending by sales or profit), not alphabetically. This ensures the most important items appear first.

**6. Preattentive attributes used intentionally:** Color, size, and position are used to draw the viewer's eye to the most important data points — not decoratively. Every color choice encodes information.
