---
name: dormant-account-analysis
description: >
  Run the Dormant Account Analysis to classify accounts as Active, Dormant, Reactivated, or New
  based on purchase history. Use this skill whenever the user asks to run the dormant analysis,
  refresh the dormant account report, update the dormant model, re-run account status analysis,
  or mentions "dormant accounts", "account dormancy", or "reactivation analysis". Also trigger
  when the user uploads new AccountMasterData.csv and TransactionMasterData.csv files and wants
  the analysis refreshed.
---

# Dormant Account Analysis

## Overview

This skill produces an Excel workbook that answers two questions:

1. **What is the right dormant threshold?** — For each inactivity window (3–36 months), what % of accounts eventually return? This validates or challenges the assumed definition of "dormant."
2. **How do accounts flow over time?** — A monthly model showing Active, Dormant (total and newly dormant), Reactivated, and New accounts, with a variable threshold dropdown and YoY comparisons.

The workbook contains four sheets: Dormant Definition, Segment Analysis, Monthly Model (with interactive threshold dropdown), and Reference Data.

## Data Requirements

The analysis expects two CSV files with these exact column names:

### AccountMasterData.csv

| Column | Description |
|--------|-------------|
| Customer Number | Unique account identifier |
| Segment | Account segment (e.g., DESIGN FIRM, SPECIALTY) |
| Sub Segment | Account sub-segment |
| IsGrandTotalRowTotal | "True" for summary rows to exclude |

Other columns (Name, State, Sales Channel, etc.) are preserved but not required for the analysis.

### TransactionMasterData.csv (samples already filtered out)

| Column | Description |
|--------|-------------|
| Customer Number | Account identifier (links to master) |
| Year | Transaction year (integer) |
| MonthNo | Transaction month number 1–12 |
| Day | Transaction day |
| Segment | Segment at time of transaction |
| Sub Segment | Sub-segment at time of transaction |
| IsGrandTotalRowTotal | "True" for summary rows to exclude |
| SumTY_Invoiced_Amount | Invoice amount ($) |
| TY_Net_Qty | Net quantity |

Segments and sub-segments are discovered dynamically from the data — they do not need to match a fixed list.

## Key Assumptions

- **$0 invoiced AND 0 qty rows are excluded.** If there's no revenue, it doesn't count as a purchase. Rows with $0 but positive qty (replacements/warranties) ARE counted.
- **Partial years are handled automatically.** The script detects if the earliest year is partial and starts the monthly model from the first full January.
- **"New" means first-ever purchase that month.** An account is new in the month of its first qualifying transaction.
- **"Reactivated" means was dormant last month, active this month, and is not new.**
- **The reconciliation always holds:** Active = Prior Active − Newly Dormant + Reactivated + New Accounts.

## How to Run

### Step 1: Locate the input files

The user will either upload new CSV files or point to existing ones. Find the paths to:
- `AccountMasterData.csv` (or similarly named account master file)
- `TransactionMasterData.csv` (or similarly named transaction file)

### Step 2: Run the analysis script

```bash
python3 SKILL_DIR/scripts/dormant_analysis.py \
  <path/to/AccountMasterData.csv> \
  <path/to/TransactionMasterData.csv> \
  <output_path/Dormant_Account_Analysis.xlsx> \
  [--start-year YYYY]
```

The `--start-year` flag is optional. If omitted, the script auto-detects the first full calendar year in the data.

The script prints progress and key metrics to stdout as it runs — share these with the user so they can confirm record counts and spot-check results.

### Step 3: Recalculate formulas

The workbook uses Excel formulas (INDEX/MATCH for the threshold dropdown, percentage calculations, YoY formulas). After generating the file, recalculate using the xlsx skill's recalc script:

```bash
python3 /sessions/great-ecstatic-pascal/mnt/.skills/skills/xlsx/scripts/recalc.py <output.xlsx> 60
```

Verify zero formula errors before delivering.

### Step 4: Deliver the workbook

Save the output to the user's workspace folder and provide a computer:// link.

## Output Structure

| Sheet | Contents |
|-------|----------|
| **Dormant Definition** | Return rate table (3–36 months), line chart, gap distribution |
| **Segment Analysis** | Return rates by Segment and Sub Segment with color-coded heatmap |
| **Monthly Model** | Interactive threshold dropdown (6/9/12/15/18/24), reconciliation columns, YoY, two charts |
| **Reference Data** | Raw monthly data for all 6 thresholds (powers the dropdown formulas) |

## Troubleshooting

- **Column names don't match**: The script expects exact column names. If the user's export has different names, rename them before running or ask the user to adjust.
- **recalc.py errors**: If LibreOffice isn't configured, the recalc script handles setup on first run. Allow up to 60 seconds.
- **Very large datasets**: The monthly model computation is O(customers × months × thresholds). For 15K+ customers and 70+ months this takes 2–5 minutes — that's normal.
