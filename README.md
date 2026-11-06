# 📊 Marketing Funnel Analysis

> Finding where visitors drop off between browsing and purchasing, and what to fix first.

![Python](https://img.shields.io/badge/Python-Jupyter-orange)
![SQL](https://img.shields.io/badge/SQL-Analysis-blue)
![Excel](https://img.shields.io/badge/Excel-Validation-green)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow)

## 📌 Project Overview

This project analyzes **10,000 visitors** moving through a four-stage e-commerce funnel (**Browse → Add to Cart → Checkout → Purchase**), calculates stage conversion rates, compares segments (channel, device, region, product category) and recommends actions to improve conversion.

**Track:** Data Analytics | **Task:** 18 – Marketing Funnel Analysis

## 🎯 Objective

Identify major funnel drop-offs and provide actionable recommendations.

## 🏆 Headline Results

| Metric | Value |
|---|---|
| Total visitors | 10,000 |
| Total purchases | 1,004 |
| **Overall conversion rate** | **10.04%** |
| Total revenue | $277,323 |
| Average order value | $276.22 |
| Biggest drop-off rate | **Checkout → Purchase (70.95% lost)** |
| Biggest drop-off volume | **Add to Cart → Checkout (3,493 users lost)** |

![Funnel](images/funnel_chart.png)

## 📂 Repository Structure

```
marketing-funnel-analysis/
├── data/
│   └── Funnel_Analysis_Data.csv        # Event-level dataset (21,409 rows)
├── sql/
│   └── funnel_analysis.sql             # SQL queries
├── images/                             # Charts used in the report
├── funnel_analysis.ipynb               # Jupyter notebook (full analysis)
├── REPORT.md                           # Detailed report & recommendations
└── README.md
```

## 🗂️ Dataset

| Column | Description |
|---|---|
| User ID / Session ID | Unique visitor and session (1 session per user) |
| Event Time | Timestamp (9 Dec 2025 – 8 Jan 2026) |
| Event | Browse, Add to Cart, Checkout, Purchase |
| Device | Desktop, Mobile, Tablet |
| Region | North, South, East, West |
| Channel | Google Ads, Email, Organic, Social Media |
| Product Category | Electronics, Beauty, Fashion, Home, Sports |
| Revenue | Order value (non-zero only on Purchase events) |
| Bonus Flag | "Yes" on every non-purchase event and "No" on every purchase, so it only mirrors the event type and is **not used** in the analysis |

**Data quality:** no missing values, no duplicates, and every user's device/region/channel is consistent. Stages are strictly sequential (no checkout without a cart, no purchase without checkout).

## 🛠️ Tools

- **Python (pandas, matplotlib, scipy)** in Jupyter for the analysis and charts
- **SQL** for funnel and segment queries
- **Excel / Power BI** for pivot validation and dashboarding (optional extension)

## 🧮 Method

1. Validate data quality.
2. Build a user-level funnel (one row per user, flags for each stage reached).
3. **Stage conversion** = users at stage ÷ users at previous stage.
4. **Overall conversion** = purchases ÷ visitors.
5. Repeat by segment and test differences with chi-square.
6. Visualize and summarize recommendations.

## 📈 Key Findings

1. **Funnel:** 10,000 → 6,949 (69.5%) → 3,456 (49.7%) → 1,004 (29.1%).
2. **Checkout → Purchase is the weakest step**: 7 in 10 users who start checkout never pay.
3. **Add to Cart → Checkout loses the most users** (3,493), half of all carts.
4. **Segments perform similarly.** Overall conversion ranges only from 9.3% to 11.2% and differences are **not statistically significant** (all p > 0.14), so the problem is funnel-wide rather than tied to one channel, device or region.
5. Directional signals worth monitoring: Mobile has the lowest checkout-to-purchase rate (27.5% vs 30.1% on desktop), and Google Ads delivers the highest revenue per visitor ($29.31).

## 💡 Recommendations

1. **Fix checkout first**: guest checkout, fewer form fields, more payment options, visible shipping cost and trust badges.
2. **Recover abandoned carts**: reminder emails/retargeting within hours (buyers complete checkout in about 3 minutes, so intent fades fast).
3. **Reduce cart friction**: show shipping/tax early and add a persistent cart.
4. **Optimize mobile checkout** and monitor it as a priority device.
5. **A/B test and track** stage-level conversion weekly, since no segment is clearly underperforming.

Full details in **[REPORT.md](REPORT.md)**.

## ▶️ How to Run

```bash
git clone https://github.com/<your-username>/marketing-funnel-analysis.git
cd marketing-funnel-analysis
pip install pandas matplotlib scipy jupyter
jupyter notebook funnel_analysis.ipynb
```

## 🎤 Interview Questions

**What is conversion rate?** The percentage of users who complete a target action out of all users who entered the funnel: `conversions ÷ visitors × 100`. Here, 1,004 ÷ 10,000 = 10.04%.

**Where would you investigate first?** At the Checkout → Purchase step, which has the highest drop-off rate (70.95%), then segment it by device, channel and region. I would also review the Add to Cart → Checkout step, which loses the most users in absolute terms.

## 👤 Author

**[Your Name]** | [LinkedIn] | [GitHub]
