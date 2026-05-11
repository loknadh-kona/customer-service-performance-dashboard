# 📖 Data Dictionary
## Dataset: 2023 Omni-Channel Customer Service & Sales Performance

---

## Sheet: Data — Raw Call Records (1,000 rows)

| Column | Data Type | Description | Sample Values |
|---|---|---|---|
| `Call number` | String | Unique identifier for each call interaction | `Call_7271`, `Call_7272` |
| `Customer ID` | String | Anonymized unique customer identifier | `C0001` – `C0015` |
| `Duration` | Integer | Call duration in **minutes** | Min: 2 · Max: 176 · Avg: 89.9 |
| `Representative` | String | Agent who handled the call | `R01`, `R02`, `R03`, `R04`, `R05` |
| `Date of Call` | Date | Date the call occurred (Excel serial format) | Full Year 2023 |
| `Purchase Amount` | Integer | Dollar value of purchase made during/after the call | Min: $20 · Max: $225 · Avg: $97 |
| `Satisfaction Rating` | Float | Customer satisfaction score (0.0 – 5.0) | Avg: 3.89 · Std Dev: 0.84 |
| `FY` | Integer | Fiscal year of the record | `2023` |
| `Day of week` | String | Day the call occurred | Monday – Sunday |
| `Duration Bucket` | String | Categorical grouping of call duration | `Under 10 mins`, `10 to 30 mins`, `30 to 60 mins`, `1 to 2 hours`, `More than 2 hours` |
| `Rating rounded` | Integer | Satisfaction rating rounded to nearest whole number | 0, 1, 2, 3, 4, 5 |

---

## Sheet: Data — Customer Demographic Lookup (15 rows)

| Column | Data Type | Description | Sample Values |
|---|---|---|---|
| `Customer ID` | String | Links to main call records | `C0001` – `C0015` |
| `Gender` | String | Customer gender (note: labeled "Gedner" in raw data — typo) | `Male`, `Female` |
| `Age` | Integer | Customer age in years | Range: 22 – 43 |
| `City` | String | Customer's regional service center | `Cincinnati`, `Cleveland`, `Columbus` |

---

## Sheet: Pivot — Aggregated KPIs

| Metric | Description |
|---|---|
| `Call Count` | Total number of calls (overall and per rep / city / month / day) |
| `Total Purchase Amount` | Sum of all purchase values in dollars |
| `Total Duration` | Sum of all call durations in minutes |
| `Average Rating` | Mean satisfaction score across all calls |
| `5* Calls` | Count of calls where rounded rating = 5 |

---

## Derived Business Metrics (Used in Dashboard)

| Metric | Calculation | Value |
|---|---|---|
| Average Handle Time (AHT) | Total Duration ÷ Call Count | 89.9 min |
| CSAT Rate (5-Star) | 5-Star Calls ÷ Total Calls | 30.7% |
| Revenue per Call | Total Revenue ÷ Call Count | $96.62 |
| Low Satisfaction Rate | Calls rated ≤ 2 ÷ Total Calls | ~8.5% |

---

## Data Quality Notes

- `Satisfaction Rating` contains one record with a value of `0` — possible data entry error or unrated call; excluded from rating averages in the dashboard
- `Date of Call` is stored as Excel serial numbers and formatted as dates within the workbook
- `Gender` column header is misspelled as `Gedner` in the raw data — treated as `Gender` throughout the dashboard
- Duration values are in minutes; the `Duration Bucket` column provides pre-categorized groupings for chart use

---

*Data Dictionary v1.0 · Customer Service Excellence & Operational Performance Dashboard*
