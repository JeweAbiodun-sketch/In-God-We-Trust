# Executive Memo: Marketing Channel Performance Analysis

**To:** Chief Marketing Officer  
**From:** Abiodun Olawuyi, Marketing Analyst  
**Date:** 2026-06-01  
**Dataset:** Digital Marketing Performance Dataset (30,000 ad records, 2023–2025)  
**Source:** HuggingFace — jason1966/alinaboulsi_digital-marketing-performance-dataset  
**Period Analysed:** Multi-year campaign data across 6 channels  

---

## Executive Summary

An analysis of 30,000 ad performance records across six marketing channels was conducted to
inform the allocation of the $500K monthly marketing budget. Statistical hypothesis testing
(independent t-tests, Fisher's exact tests) confirmed that channel performance differences
are real and not due to random variation — 12 of 15 CPA pairs and all 15 conversion-rate
pairs remain significant after Bonferroni and Benjamini-Hochberg FDR correction.

**Google Search stands out as the only channel generating positive ROI** (ROAS 3.78,
profit +$7.6M). LinkedIn is the worst performer by every metric. Meta, TikTok, and
Snapchat form a mid-tier cluster with statistically similar CPA but real differences
in conversion rate.

---

## Key Findings

### 1. Channel Performance Summary

| Platform       | Total Spend    | CPA (agg) | Mean Daily CPA     | 95% CI (daily CPA) | ROAS | Conv Rate | Profit         |
|----------------|----------------|-----------|--------------------|---------------------|------|-----------|----------------|
| Google Search  | $2,744,251     | $12.66    | $90.65             | [$80.57 – $101.46]  | 3.78 | 1.88%     | **+$7,617,924** |
| Meta           | $2,636,603     | $62.81    | $228.71            | [$205.78 – $252.95] | 0.62 | 0.95%     | –$996,497      |
| Snapchat       | $1,450,866     | $68.61    | $255.40            | [$231.66 – $282.48] | 0.46 | 0.65%     | –$781,129      |
| TikTok         | $2,091,252     | $73.95    | $247.06            | [$222.46 – $272.89] | 0.48 | 0.72%     | –$1,097,391    |
| Google Display | $1,157,077     | $127.03   | $349.54            | [$322.06 – $380.50] | 0.28 | 0.50%     | –$828,572      |
| LinkedIn       | $2,556,361     | $457.47   | $913.53            | [$833.43 – $984.71] | 0.11 | 0.82%     | –$2,279,390    |

> Note: daily CPA means are higher than aggregate CPA because many daily records have zero
> conversions (CPA = undefined/excluded), inflating the daily average relative to the
> total-spend / total-conversion aggregate. Aggregate CPA is the more reliable efficiency
> metric for budget planning.

### 2. Statistically Significant Differences (after multiple-comparison correction)

**CPA t-tests (15 pairwise comparisons):**
- 12 / 15 pairs significant after both Bonferroni and BH FDR correction  
- 3 non-significant pairs: Meta vs Snapchat (p=0.13), Meta vs TikTok (p=0.29),
  Snapchat vs TikTok (p=0.64) — these three channels form a statistically
  **indistinguishable CPA cluster**

Largest effects (Cohen's d ≥ 0.8 = large):
| Pair                        | CPA A    | CPA B    | Cohen's d | Interpretation |
|-----------------------------|----------|----------|-----------|----------------|
| Google Search vs LinkedIn   | $90.65   | $913.53  | 1.11      | Large          |
| LinkedIn vs Meta            | $913.53  | $228.71  | −0.88     | Large          |
| LinkedIn vs Snapchat        | $913.53  | $255.40  | −0.85     | Large          |
| LinkedIn vs TikTok          | $913.53  | $247.06  | −0.86     | Large          |

**Conversion rate Fisher's exact tests (15 pairs):**
- All 15 pairs significant after Bonferroni and BH FDR correction
- Google Search conversion rate (1.88%) is 2× Meta's (0.95%), nearly 3× Snapchat's (0.65%)
- All differences are practically meaningful, not just statistically significant

### 3. Data Adequacy (Power Analysis)

| CPA Difference | 90-Day Power | Min Days for 80% Power |
|----------------|--------------|------------------------|
| 5%             | 60.6%        | 180 days               |
| 10%            | 99.0%        | 60 days                |
| 15%            | 100.0%       | 30 days                |
| 20%            | 100.0%       | 30 days                |

All 12 FDR-significant CPA pairs had observed differences ≥ 26%, yielding **100% power
at 90 days**. The dataset is more than adequate for detecting the observed differences.

---

## Recommendations

### Budget Allocation — $500K Monthly

Channels were ranked by composite score (50% CPA rank + 50% conversion-rate rank),
with minimum/maximum guardrails applied.

| Platform       | Composite Score | Allocation  | % of Budget | Rationale |
|----------------|-----------------|-------------|-------------|-----------|
| Google Search  | 6.0 / 6.0       | **$200,000** | **40.0%**   | Only profitable channel; large effect, high conversion |
| Meta           | 5.0 / 6.0       | $125,000    | 25.0%       | Largest reach, best efficiency outside Google Search   |
| TikTok         | 3.0 / 6.0       | $60,000     | 12.0%       | Statistically tied with Snapchat on CPA; strong scale  |
| Snapchat       | 3.0 / 6.0       | $60,000     | 12.0%       | Same CPA cluster as TikTok; audience diversification   |
| Google Display | 1.5 / 6.0       | $30,000     | 6.0%        | Retargeting and awareness value; low direct efficiency |
| LinkedIn       | 2.5 / 6.0       | $25,000     | 5.0%        | Retain only for B2B / brand-safety objectives          |
| **Total**      |                 | **$500,000**| **100%**    | |

> **Google Search is boosted above its raw composite share** (28.6% → 40%) because it is
> the only channel with ROAS > 1 and is the primary profit driver. LinkedIn is reduced
> below its composite share due to extreme CPA and negative ROAS; it is retained at a
> minimal floor only if B2B targeting has strategic value not captured in direct conversions.

### Strategic Actions

1. **Google Search: scale with controlled expansion.** Increase daily budgets in top-ROAS
   campaigns and monitor CPA / ROAS weekly for diminishing returns.

2. **Meta: optimise for conversion objectives.** The channel has the best reach among
   non-search platforms and a respectable 0.95% conversion rate. Shift budget from
   awareness to conversion-focused ad sets.

3. **TikTok & Snapchat: treat as a single cluster.** Their CPA difference is statistically
   indistinguishable (p=0.64). Allocate equally and run a 90-day head-to-head test if
   channel separation is desired.

4. **LinkedIn: conduct a hold-out test before increasing spend.** The $913 CPA is
   statistically significant and very large (Cohen's d ≥ 0.85 vs all other channels).
   If LinkedIn is retained for brand or B2B reasons, implement strict CPA caps.

5. **Google Display: use for retargeting only.** Direct-response ROAS of 0.28 is
   poor; this channel's value may lie in assisted conversions not measured here.

---

## Statistical Caveats

**Dataset limitations**
- Source: synthetic/simulated dataset on HuggingFace. Patterns reflect the data
  generator's assumptions, not a real advertiser's media mix.
- Attribution: only direct (last-click) conversions are recorded. Upper-funnel channels
  (Google Display, TikTok, LinkedIn) are disadvantaged because their awareness-stage
  value is not captured.
- Time period: ad records span 2023–2025, during which auction dynamics, CPMs, and
  consumer behaviour changed; pooling all years may obscure trend shifts.

**Multiple comparisons**
- 30 total hypothesis tests were performed (15 CPA t-tests + 15 Fisher's exact tests).
- Bonferroni correction divides alpha by the number of tests; BH FDR controls the
  expected proportion of false discoveries. Both methods were applied.
- For CPA: all 12 significant pairs survive both corrections — zero false positives
  are expected.
- For conversion rates: all 15 pairs survive both corrections; Fisher's exact test
  is exact (not approximate), so the results are robust.

**Confidence intervals**
- Bootstrap 95% CIs were computed from daily CPA distributions (1,000 resamples).
  Non-overlapping CIs between Google Search and all other channels confirm the
  significance found in the t-tests.

**Statistical vs. practical significance**
- Meta vs Snapchat (p=0.13, d=0.07) and related pairs: negligible Cohen's d means
  the difference is not practically meaningful even if it were significant.
- A large p-value does NOT mean the channels are identical — it means the data are
  insufficient to distinguish them. Budget decisions for this cluster should rest on
  audience, creative, and strategic fit, not CPA alone.

**Power analysis limitations**
- Simulations assume CPA is normally distributed with 15% standard deviation.
  Actual CPA distributions are right-skewed; true power may differ slightly.
- Power > 80% for all observed effect sizes (≥ 26%) with 90 days of data, so data
  adequacy is not a concern for the current findings.
- Detecting a 5% CPA improvement requires ~180 days of data (power = 89%); smaller
  optimisation signals should not be acted upon without more data.

---

## Next Steps

1. Run incremental lift tests for Google Search scale-up before committing full $200K
2. Set up weekly CPA monitoring dashboards per channel with alert thresholds
3. Conduct a 90-day head-to-head test: TikTok vs Snapchat (equal budget split)
4. Evaluate LinkedIn with a 60-day brand-lift study using hold-out control group
5. Obtain multi-touch attribution data to properly credit upper-funnel channels
6. Re-run this analysis after budget reallocation to confirm expected improvements

---

*Prepared by Abiodun Olawuyi — Marketing Analysis | 2026-06-01*
