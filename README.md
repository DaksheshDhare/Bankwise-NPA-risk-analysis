# Bank-wise NPA Risk Analysis

22 years of RBI data across 144 Indian banks, used to build a risk segmentation framework that separates individual bank soundness from systemic financial stability risk.

## Why this project

Ranking banks by NPA ratio alone is misleading, it puts tiny foreign banks with almost no real India footprint at the top of the "riskiest" list. This project builds a more honest, two-lens framework: which banks are individually distressed, versus which banks actually matter for financial system stability.

## Data source

Reserve Bank of India, "Bank-wise and Bank Group-wise Gross Non-Performing Assets, Gross Advances, and Gross NPA Ratio of Scheduled Commercial Banks," 2004–2025.
Source: [rbi.org.in](https://rbi.org.in) → Statistical Tables Relating to Banks in India

## What's in this repo

| File | Description |
|---|---|
| `NPA_Risk_Analysis_Report.md` | Full write-up: methodology, findings, and limitations |
| Power BI dashboard (6 visuals) | Trend, ranking, scatter, and merger-comparison charts |

## Data cleaning summary

- Removed footnote text that had been pulled into the data as if it were actual rows
- Separated individual banks from bank-group subtotals (Public Sector, Private Sector, Foreign, Small Finance) using a tagged Row Type column, to prevent double counting
- Tagged the 6 banks affected by RBI's 2020 forced mergers (Oriental Bank of Commerce and United Bank of India into PNB, Syndicate Bank into Canara Bank, Allahabad Bank into Indian Bank, Andhra Bank and Corporation Bank into Union Bank), since these mergers create a structural break in any bank's individual history
- Calculated NPA Ratio directly from Gross NPAs ÷ Gross Advances where the source column was unavailable, rather than leaving it blank
- Converted "-" placeholder values to nulls rather than zero

## Key findings

- **System-wide NPA ratio fell 73% since COVID**: 8.21% in 2020 to 2.22% in 2025, a consistent year-over-year improvement with no reversals.
- **Public Sector Banks had the clearest crisis-and-recovery story**: NPA ratio peaked around 14.7% in 2018 (India's known bad-loan crisis period) and converged to 2–3% by 2025, in line with other bank groups.
- **The highest raw NPA ratios are misleading**: banks like Sberbank and Sonali Bank show 40%+ ratios, but on loan books of tens of crores, not systemically meaningful. Lakshmi Vilas Bank is the one genuine distress case in the top 10, and it was already resolved via forced merger in 2020.
- **The 2020 forced mergers did not spike risk uniformly**: Indian Bank showed a clear post-merger jump after absorbing Allahabad Bank; Punjab National Bank and Union Bank of India stayed roughly flat despite each absorbing two banks.
- **Ranked by absolute exposure (Gross NPA amount, not ratio)**, the real regulatory priority list is State Bank of India, Punjab National Bank, Union Bank of India, Canara Bank, and Bank of India, largely a function of scale, not disproportionate risk.

## Tools used

Excel, Power Query, Power BI

## Known limitations

- Individual loan-level default data is not publicly available in India; this analysis works at the bank and bank-group level, not individual borrower level.
- Bank coverage and reporting format changed over the 22-year window (e.g. Public Sector Banks as a unified category only exists from 2018 onward), so early and recent years are not perfectly like-for-like.
