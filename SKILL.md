---
name: fundamental-company-analysis
description: Analyse a listed company's fundamentals across profitability, financial position, returns and valuation (revenue growth, EBITDA, EBITDA margin, PAT, PAT margin, EPS, debt-to-equity, current ratio, ROE, ROCE, ROA, P/E, P/B, earnings yield) and explain the results neutrally. Use this skill whenever the user provides company financial figures with a share price or asks for fundamental analysis, a stock's financial snapshot, valuation multiples, returns on capital, or "analyse this company", even if they do not use the words "fundamental analysis".
---

# Fundamental Company Analysis

This skill turns a company's financial figures and market data into a structured fundamental analysis in four parts: profitability, financial position, returns and valuation.

## Inputs

- Income statement, current year and (optionally) previous year: revenue, operating profit (EBIT), depreciation and amortisation, profit after tax (PAT)
- Balance sheet, current year: total assets, shareholders' equity, borrowings, current assets, current liabilities
- Market data: number of shares, current share price; optionally peer median P/E, peer median P/B and a benchmark bond yield

State the unit of the figures (Rs, Rs thousands, Rs lakhs, Rs crore or Rs millions) and the unit of the share count. Per-share figures are in rupees.

## Formulas (use exactly these)

| Part | Measure | Formula |
|---|---|---|
| Profitability | Revenue growth | (Current revenue - Previous revenue) / Previous revenue x 100 |
| Profitability | EBITDA | Operating profit (EBIT) + Depreciation and amortisation |
| Profitability | EBITDA margin | EBITDA / Revenue x 100 |
| Profitability | PAT margin | PAT / Revenue x 100 |
| Profitability | EPS | PAT / Number of shares (in rupees per share) |
| Financial position | Debt-to-equity | Borrowings / Shareholders' equity |
| Financial position | Current ratio | Current assets / Current liabilities |
| Returns | ROE | PAT / Shareholders' equity x 100 |
| Returns | ROCE | EBIT / (Total assets - Current liabilities) x 100 |
| Returns | ROA | PAT / Total assets x 100 |
| Valuation | P/E | Share price / EPS |
| Valuation | P/B | Share price / Book value per share, where book value per share = Shareholders' equity / Number of shares |
| Valuation | Earnings yield | EPS / Share price x 100 |

Optional valuation context:
- P/E or P/B premium or discount to peers = (Company multiple / Peer median multiple - 1) x 100
- Earnings yield spread = Earnings yield - Benchmark bond yield, in percentage points

Rules for calculation:
- Calculate a measure only when every figure it needs is provided. Leave out any measure that cannot be calculated and say why. Never assume a missing figure.
- If a denominator is zero, the measure is not defined. Do not divide by zero.
- If shareholders' equity is zero or negative, debt-to-equity, ROE and P/B are not meaningful.
- If capital employed (total assets less current liabilities) is zero or negative, ROCE is not meaningful.
- If EPS is zero or negative, P/E is not meaningful.
- Ratios use closing (year-end) balances, not averages. Say so when relevant.
- When figures are supplied already calculated (for example by an application), use them exactly as given. Never recalculate, round differently or change a number.

## Data checks

If check results are supplied (for example, current assets above total assets), report each failed check first and say the analysis depends on figures that need verifying. Do not try to correct the figures.

## Interpretation rules

- Separate facts (what the numbers are) from observations (what they may indicate).
- Never state a cause as fact. Numbers show what changed, not why. Suggest possible factors only as items to verify.
  - Do not say: "PAT margin fell because costs rose."
  - Say instead: "PAT margin fell. The cost structure is one factor to review if the detail is available."
- A multiple such as P/E or P/B is not cheap or expensive by itself. It needs a peer or historical comparison, and industries differ. If peer figures are supplied, describe the premium or discount only as a comparison, not as a verdict.
- Do not recommend buying, selling or holding. Do not give a price target, investment, tax or legal advice, and do not predict future performance.
- Use neutral, professional language.

## Output format

In application mode, where the tables and ratios are already displayed, write only these sections in plain text (no markdown symbols), under 350 words in total, with each title on its own line:
1. Profitability (2 to 3 short lines starting with a hyphen)
2. Financial Position (1 to 2 lines)
3. Returns (1 to 2 lines)
4. Valuation (2 to 3 lines, including any peer or bond-yield comparison supplied)
5. Points to Verify (up to 4 lines, including failed checks, missing measures and the need for a benchmark)

For a full standalone analysis, show each formula with its calculation.

## Accuracy rules

- Use only the figures provided. Do not invent, assume or adjust any figure.
- Mention the unit once, near the start.
- If information is missing, name exactly what is missing and which measure it prevents.

## Worked example

Input (Rs crore): Revenue previous 1,000, current 1,200. EBIT previous 150, current 190. Depreciation and amortisation previous 40, current 50. PAT previous 100, current 130. Total assets 1,500. Equity 800. Borrowings 250. Current assets 600. Current liabilities 350. Shares 20 crore. Share price Rs 130. Peer P/E 22, peer P/B 3.0, bond yield 7.0%.

Expected results:
- Revenue growth = (1,200 - 1,000) / 1,000 x 100 = 20%
- EBITDA = 240 (previous 190); EBITDA margin = 20% (previous 19%)
- PAT margin = 10.83% (previous 10%)
- EPS = 130 crore / 20 crore shares = Rs 6.50
- Debt-to-equity = 250 / 800 = 0.31x; Current ratio = 600 / 350 = 1.71x
- ROE = 130 / 800 = 16.25%; ROCE = 190 / (1,500 - 350) = 16.52%; ROA = 130 / 1,500 = 8.67%
- P/E = 130 / 6.5 = 20.0x; book value per share = Rs 40; P/B = 3.25x; Earnings yield = 5.0%
- P/E is 9.09% below the peer median; P/B is 8.33% above it; earnings yield is 2.0 percentage points below the bond yield

The commentary should state these as facts, note that valuation depends on peer and historical context, and list items to verify without naming causes.

## Self-check before answering

- Does every number come from the input or the supplied calculations?
- Were any missing figures assumed? (They must not be.)
- Is there any buy, sell or hold language, price target or causal claim? (There must not be.)
- Are failed checks and uncalculated measures mentioned?
- Is the unit stated, and is the output within the length and format?
