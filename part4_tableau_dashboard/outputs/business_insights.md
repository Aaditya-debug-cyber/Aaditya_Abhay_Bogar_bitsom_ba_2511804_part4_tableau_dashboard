# Business Insights from Executive Dashboard
**Analyst:** Aaditya Abhay Bogar (bitsom_ba_2511804)  
**Date:** 2026-06-19  
**Dataset:** dashboard_sales_data.xlsx | 4,200 orders | Jan 2024 – Dec 2025

---

## Calculated Fields Created in Tableau

| Calculated Field | Formula | Purpose |
|---|---|---|
| Profit Margin | `SUM([profit]) / SUM([sales])` | Measures profitability efficiency per rupee of sales |
| Cost | `[sales] - [profit]` | Derives cost of goods from sales and profit |
| Return Rate | `SUM([return_flag]) / COUNT([order_id])` | Percentage of orders returned |
| Avg Order Value | `SUM([sales]) / COUNTD([order_id])` | Average revenue per distinct order |
| Shipping Delay Bucket | IF/ELSEIF on delivery_days | Categorizes delivery speed into 5 groups |
| Profit per Order | `SUM([profit]) / COUNT([order_id])` | Average profit contribution per transaction |
| Discount Band | IF/ELSEIF on discount | Groups discount levels for pattern analysis |

---

## Insight 1 — Sales Trend: Strong 2025 Second Half Recovery

**Observation:** Monthly sales dipped in April 2025 (₹7.2M) and June 2025 (₹7.3M), but recovered strongly with July (₹10.7M) and August (₹10.9M) — the highest months in the 2-year dataset.

**Data evidence:** July 2025 = ₹10.66M, August 2025 = ₹10.86M vs trough of ₹7.19M in April 2025.

**Business interpretation:** The H2 2025 recovery aligns with seasonal demand patterns. August being the highest month across both years suggests back-to-office and pre-festive purchasing drives significant volume.

**Recommended action:** Increase inventory pre-stocking and marketing spend in June–July to amplify the natural H2 surge. Investigate what caused the April dip — whether it is structural (low-season) or driven by supply disruptions.

---

## Insight 2 — Regional Performance: South Dominates, East Underperforms

**Observation:** South region generates the highest sales (₹64.7M, 29.8% of total) and profit (₹10.0M). East region lags at ₹48.9M in sales (22.5% of total).

**Data evidence:** South = ₹64,693,707 sales | East = ₹48,859,164 sales | Difference = ₹15.8M (32% more in South vs East).

**Business interpretation:** South region either serves a larger addressable market or has a more effective sales mix. The gap is not solely attributable to order count (South has 1,210 orders vs East's 897) — average order value is also higher in South.

**Recommended action:** Review East region store-level data for underperformers. Consider whether the South's category or channel mix (Referral and Email channels may perform differently by region) can be replicated in the East.

---

## Insight 3 — Category Profitability: Technology Carries the Business

**Observation:** Technology generates ₹153.9M in sales (70.9% of total) and ₹28.0M in profit (84.2% of total profit). Furniture contributes only 3.4M in profit despite ₹51.6M in sales.

**Data evidence:** Technology margin = 18.2% | Furniture margin = 6.9% | Office Supplies margin = 14.9%.

**Business interpretation:** Furniture is a volume contributor but a profit drag. At 6.9% margin, Furniture barely covers costs relative to the resources it consumes (storage, shipping, returns). Technology and Accessories/Phones/Copiers are the real profit engines.

**Recommended action:** Leadership should consider reducing Furniture inventory depth and redirecting shelf space and marketing budget toward high-margin Technology sub-categories (Accessories: 18.3%, Phones: 18.5%, Copiers: 18.0%).

---

## Insight 4 — Sub-Category Profitability: Tables and Bookcases Are Margin Killers

**Observation:** Tables (margin 5.7%) and Bookcases (margin 5.7%) are the weakest sub-categories. Together they represent ₹25.4M in sales but only ₹1.44M in profit — well below the company-wide margin of 15.35%.

**Data evidence:** Tables profit = ₹731,534 on ₹12.9M sales | Bookcases = ₹711,733 on ₹12.5M sales.

**Business interpretation:** These sub-categories likely carry high shipping costs (bulky items), high return rates, and steep discounting to remain competitive. They dilute the overall portfolio margin.

**Recommended action:** Audit the cost structure of Tables and Bookcases. If logistical costs cannot be reduced, consider whether these sub-categories should remain in the product portfolio at all.

---

## Insight 5 — Discount Impact: Discounts above 30% Generate Losses

**Observation:** Orders with discounts of 31–40% generate an average profit of -₹1,601 per order — the only discount band with a negative average profit.

**Data evidence:**
- No discount: avg profit = ₹13,203/order
- 1-10% discount: avg profit = ₹10,010/order
- 11-20%: ₹6,336/order
- 21-30%: ₹3,181/order
- 31-40%: **-₹1,601/order (loss)**

**Business interpretation:** Heavy discounting is destroying value. While discount may drive volume, it destroys margin faster than it generates incremental sales. The 13.7% average discount across the portfolio is already compressing margins significantly.

**Recommended action:** Cap maximum discount at 25% as a policy rule. Require management approval for any discount above 20%. Analyze which salespeople or regions are applying the deepest discounts.

---

## Insight 6 — Shipping Performance: Standard Class Has Highest Delivery Days

**Observation:** Standard Class (58% of all orders) averages 4.2 delivery days. Same Day delivery averages 0.3 days. 2,435 orders use Standard Class.

**Data evidence:** avg_delivery_days — Standard Class: 4.2d | Second Class: 3.9d | First Class: 2.9d | Same Day: 0.3d.

**Business interpretation:** With 58% of orders on Standard Class at 4.2-day average delivery, there is a significant delivery experience gap for the majority of customers. In an era of next-day delivery expectations, this could be contributing to customer satisfaction issues and returns.

**Recommended action:** Analyze whether the 4.2-day average can be reduced through regional warehouse optimization. Offer proactive shipping upgrades to high-value orders (above ₹50,000) at minimal incremental cost.

---

## Insight 7 — Return Pattern: Furniture Returns Are 2.5× Higher Than Technology

**Observation:** Furniture has a return rate of 7.67% vs Technology's 3.03%. Home Office and Corporate segments also show slightly higher return propensity.

**Data evidence:** Furniture return rate = 7.67% | Office Supplies = 3.65% | Technology = 3.03%.

**Business interpretation:** Furniture returns likely stem from product fit issues (size, assembly difficulties), quality expectations, or damage during shipping. Each return in Furniture represents a high-cost reverse logistics event on top of an already low-margin product.

**Recommended action:** Add product dimensions and assembly difficulty indicators to Furniture product pages. Offer virtual room planning tools to reduce "doesn't fit" returns. Review packaging quality for Tables and Chairs (highest-ticket Furniture items).

---

## Insight 8 — Business Risk: 13.7% Average Discount with Declining Profitability Is Unsustainable

**Observation:** The average discount across all orders is 13.7%. When combined with Furniture's low margin (6.9%) and the fact that 31-40% discounts generate losses, the portfolio has a structural profitability risk if discount levels increase.

**Data evidence:** 13.7% avg discount | Overall margin 15.35% | Furniture margin 6.9% | Loss-generating discount band: 31-40%.

**Business interpretation:** If the discount culture continues to drift upward (as is common in competitive retail environments), margin compression will accelerate. The relatively thin cushion between the average margin (15.35%) and the average discount (13.7%) leaves little room for operational cost increases.

**Recommended action:** Set a company-wide discount governance policy. Track margin by discount band on a monthly basis in the dashboard. Flag any segment, region, or salesperson applying discounts that push expected profit below 10%.

---

## Insight 9 — Customer Segment: Home Office Leads, Segments Are Nearly Balanced

**Observation:** Home Office generates the highest sales (₹74.5M) and profit (₹11.6M). Corporate and Consumer are very similar in both metrics.

**Data evidence:** Home Office = ₹74.5M sales | Corporate = ₹70.6M | Consumer = ₹71.9M. Profit margins are similar across all three (~15.3%).

**Business interpretation:** The business is well-diversified across customer segments — no single segment is over-dependent. However, Home Office's slight lead may reflect work-from-home trends driving demand for Technology and Office Supplies.

**Recommended action:** Target Home Office customers with Technology bundles (monitor + keyboard + accessories). This segment shows the highest average order value potential and is likely to respond to cross-sell campaigns.

---

## Insight 10 — Campaign Channel: Organic Leads in Volume but Paid Deserves ROI Analysis

**Observation:** Organic channel drives the most orders (1,694, ~40% of total). Paid channel has 849 orders. Campaign channel distribution is not uniform across regions.

**Business interpretation:** Heavy reliance on Organic acquisition (40%) is cost-efficient but fragile. A change in search algorithm or competitor advertising surge could disrupt acquisition. Paid channel ROI (849 orders / spend invested) needs to be tracked.

**Recommended action:** Add campaign channel as a filter in the executive dashboard. Track profit per order by channel to determine which channel delivers the highest LTV customers, not just the most orders.
