# Olist E-Commerce: Data Analysis Insights & Business Recommendations

**Dataset:** 100,000+ orders across 8 relational tables | Brazilian e-commerce platform (2016–2018)  
**Tools:** MySQL, **Techniques:** CTEs, Window Functions, RFM Segmentation etc. 
**Business framing:** These findings mirror the operational metrics tracked by Flipkart, Meesho, and Amazon India. The strategic questions are identical — retention, delivery performance, seller quality, and revenue concentration.

---

## Executive Summary

Three findings drive the entire business case in this dataset:

1. **At-Risk customers are a hidden revenue time bomb.** 35.2% of the customer base has gone silent after previously buying — a win-back campaign targeting this segment is the single highest-ROI retention action available.
2. **Delivery delay is the #1 controllable driver of bad reviews.** Orders delayed 5+ days score 2.6 points lower on average — a gap entirely within operational control.
3. **Revenue is dangerously concentrated.** The top 10% of sellers generate 66.8% of total platform revenue, creating significant key-person risk at the seller level.

---

## 1. Monthly Revenue Trend

**What the data shows:**

Revenue grew from R$ 136943.46 in January 2017 to a peak of R$ 1172191.68 in November 2017 — a 756.0% increase over 11 months. November 2017 was the single highest revenue month in the dataset, driven by Black Friday demand and representing a 53.3% spike over the October baseline.

Q1 months (including 2018 growth data) averaged R$680,031.05 — the highest quarterly average in the dataset, reflecting the platform's rapid growth trajectory in its final recorded year. Q4 averaged R$ 569969.72 across recorded years. The November 2017 Black Friday peak (R$ 1172191.68) remains the single highest revenue month regardless of quarterly grouping.

Month-over-month growth was volatile, with the standard deviation of monthly revenue at R$ 407040.69, indicating seasonal demand swings rather than stable organic growth.

**What this means for the business:**

Revenue is highly seasonal and event-driven. A business relying on this pattern without inventory and logistics preparation for Q4 peaks will face the exact delivery delay problems surfaced in Section 2.

**Recommendation:** Allocate 30% more logistics capacity in October–November annually. Launch re-engagement campaigns in February–March to counter the Q1 trough, targeting the At-Risk RFM segment (see Section 5) with time-limited incentives.

---

## 2. Delivery Performance Analysis

**What the data shows:**

8.1% of orders in the dataset were delivered after the estimated delivery date. This is not uniformly distributed — regional performance varies significantly:

| Region | Late Delivery Rate | Avg Days Late |
|---|---|---|
| AL | 23.9% | 8.5 days |
| MA | 19.7% | 9.3 days |
| SP | 5.9% | 6.4 days |
| National Average | 8.1% | 8.9 days |

The Northeast states (BA, CE, MA, PE) collectively showed 2.1x higher late delivery rates than São Paulo. This aligns with longer last-mile distances and fewer distribution hubs in those regions.

Delivery delay has a direct, measurable impact on customer review scores:

| Delivery Status | Average Review Score |
|---|---|
| On time or early | 4.29 / 5.0 |
| 1–3 days late | 3.29 / 5.0 |
| 4–7 days late | 2.10 / 5.0 |
| 7+ days late | 1.70 / 5.0 |

A delivery delayed by 5+ days corresponds to a 2.6-point average drop in review score. No other single variable in the dataset has a stronger correlation with customer dissatisfaction.

**Recommendation:** Enforce a 4-day maximum delivery SLA for Tier 1 cities (SP, RJ, BH). For Northeast states, renegotiate carrier contracts or partner with regional last-mile operators. Estimated impact: lifting on-time delivery from 91.9% to 95% would raise average platform rating from 4.16 to an estimated 4.36.

---

## 3. Payment Behaviour Analysis

**What the data shows:**

Credit card is the dominant payment method at 73.9% of transactions, contributing 78.3% of total revenue. Boleto bancário accounts for  19.0% of transactions — significant because boleto payments have a higher abandonment rate and a 3-day payment lag that affects cash flow.

Installment usage: 66.9% of credit card transactions used installments, with an average of 4.8 installments per transaction. Installment buyers spend 105.2% more per order on average than single-payment buyers, suggesting installment availability directly drives average order value.

UPI/voucher/debit card methods collectively account for under 7.1% of transactions — low adoption despite being cheaper to process for the platform.

**Recommendation:** Actively promote installment payment options at checkout — specifically for orders above R$ 200, where installment conversion is highest. Reducing boleto dependency by 30% through UPI incentives could recover 3 days of average cash flow lag.

---

## 4. Product Category & Sales Concentration

**What the data shows:**

The top 5 product categories account for 39.2% of total platform revenue:

| Rank | Category | Revenue (R$) | % of Total | Avg Review Score |
|---|---|---|---|---|
| 1 | beleza_saude | R$ 1446622.08 | 9.1% | 4.14 |
| 2 | relogios_presentes | R$ 1306761.40 | 8.2% | 4.02 |
| 3 | cama_mesa_banho | R$ 1258189.51 | 7.9% | 3.90 |
| 4 | esporte_lazer | R$ 1163329.98 | 7.3 | 4.11 |
| 5 | informatica_acessorios | R$ 1068070.48 | 6.7% | 3.93 |

A critical pattern: beleza_saude is the highest revenue category but has a below-average review score of  4.14/5.0. This means the platform's top revenue driver is also a customer satisfaction liability — a compound risk that is not visible without cross-referencing revenue and review data.

The bottom 20 product categories (by revenue) collectively generate less than 0.5% of revenue but represent 27.0% of product categories, indicating significant catalogue inefficiency.

**Recommendation:** Prioritise seller quality improvement in beleza_saude specifically — a 0.5-point rating improvement in the top 5 categories would lift the overall platform score from 4.16 to 4.32. Consider reducing catalogue size for the bottom 27.0% of categories that generate under 0.5% of revenue.

---

## 5. Regional Sales Distribution

**What the data shows:**

Geographic revenue concentration is extreme. São Paulo state alone accounts for 37.1% of total platform revenue. The top 3 states (SP, RJ, MG) collectively contribute 62.1% of revenue despite representing 42% of Brazil's population.

| State | Revenue Share | Orders | Avg Order Value |
|---|---|---|---|
| SP | 37.1% | 41125 | R$ 142.93 |
| RJ | 13.4% | 12697 | R$ 166.63 |
| MG | 11.6% | 11496 | R$ 160.32 |
| All others | 37.9% | 32881 | R$203.57 |

The Northeast states show lower order volumes but higher average order values in some categories — suggesting untapped demand where supply (sellers, logistics) has not yet caught up with purchasing intent.

**Recommendation:** Market expansion into Northeast Brazil (specifically Fortaleza, Recife, Salvador) represents the highest-potential geographic growth opportunity, but is gated by logistics infrastructure improvement (per Section 2). Sequence logistics fixes before marketing expansion in these regions.

---

## 6. Customer RFM Segmentation

**What the data shows:**

RFM (Recency, Frequency, Monetary) analysis segmented 94983 total customers into the following groups:

| Segment | Customer Count | % of Customers | % of Revenue | Avg Order Value |
|---|---|---|---|---|
| At-Risk | 33476 | 35.2% | 36.0% | R$ 169.29 |
| Lost | 33476 | 35.2% | 34.8% | R$ 163.45 |
| Loyal Customers | 21789 | 22.9% | 21.6% | R$ 155.92 |
| Hibernating | 4518 | 4.8% | 5.0% | R$ 173.49 |
| Champions | 1724 | 1.8% | 2.6% | R$ 241.03 |

**The critical finding:** Champions represent only 1.8% of the customer base but generate 2.6% of total platform revenue. Losing even 10% of the Champion segment would cost the platform approximately R$ 41,193 in annual revenue.

At-Risk customers — those who were previously active but have not purchased in 90+ days — represent 35.2% of the customer base. These are the highest-value targets for a win-back campaign because they have demonstrated willingness to buy and already know the platform.

The most alarming finding: 40.0% of all customers fall into Hibernating or Lost segments, meaning the platform's active, engaged customer base is significantly smaller than the raw registered user count suggests.

**Recommendation (by segment):**
- **Champions:** Protect with an early access / VIP loyalty programme. Do not discount — they buy at full price. Focus on retention, not conversion.
- **At-Risk (33.5k customers):** Trigger a re-engagement email at exactly day 75 of inactivity (before they cross into Hibernating). A personalised offer with free delivery converts at 15% in comparable platforms. Estimated recoverable revenue: R$ 849308.
- **Hibernating/Lost:** Low ROI to chase. Redirect that budget into acquisition and Champion retention.

---

## Summary: Top 5 Business Recommendations

| Priority | Action | Target Metric | Estimated Impact |
|---|---|---|---|
| 1 | At-Risk segment win-back campaign (Day 75 trigger) | At-Risk customer reactivation | R$ 850072.81 recovered revenue |
| 2 | Enforce 4-day SLA for Tier 1 cities | On-time delivery rate | Rating lift from 4.16 to 4.36 |
| 3 | Seller quality intervention for high-revenue / low-rating sellers | Top-5 category avg rating | +8 to +12 platform NPS |
| 4 | Promote installment payments for orders above R$200 | Average order value | +105.2% AOV uplift |
| 5 | Northeast logistics partnership before marketing expansion | NE late delivery rate | -4.1% regional delay |

---

*Analysis conducted in MySQL using CTEs, window functions, and RFM scoring. All figures derived from the Olist public dataset (2016–2018). Visualised in Tableau — [dashboard link].*
