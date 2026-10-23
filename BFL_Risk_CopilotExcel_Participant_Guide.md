# Copilot in Excel — Participant Exercise Guide
### Formulas & Pivot Tables for Risk Case Monitoring
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `BFL_Risk_Copilot_Demo.xlsx`

---

## Before You Begin

- Use **Copilot agent** to open the agent in the Copilot panel
- Add `BFL_Risk_Copilot_Demo.xlsx` from OneDrive
- Keep the Copilot panel open throughout all exercises
- The file has **25 rows of risk case data** — one sheet, no formula columns yet
- Columns N–R are intentionally blank — you will fill these using Copilot

### Dataset Overview

| Column | Field | Description |
|--------|-------|-------------|
| A | Case ID | Unique case reference (RSK-001 to RSK-025) |
| B | Branch/Region | Branch or region where the case originated |
| C | Branch Code | Short branch identifier |
| D | Zone | West / North / South / East / Central |
| E | Case Type | Credit Risk Review, Fraud Investigation, Collateral Revaluation, Policy Exception Review, Portfolio Watchlist Review |
| F | Risk Analyst | Staff member handling the case |
| G | Case Flagged Date | When the case was raised for review |
| H | Case Resolved Date | When it was cleared (blank if still open) |
| I | Days in Review (TAT) | Actual number of days the case has taken |
| J | Review SLA (Days) | Benchmark review time for that case type |
| K | Customer Segment | Retail, SME, Corporate, HNI |
| L | Priority | Normal, High, Urgent |
| M | Status | Closed, Pending, Escalated |
| **N–R** | *(blank)* | **You will add these using Copilot** |

A small **Case Type Reference Table** sits to the right of the main data, in columns **U–W** (row 2 onward): Case Type, Standard Review SLA (Days), and Escalation Owner. You'll use this in Exercise 5 for the VLOOKUP exercise.

---

## Exercise 1 — Add a Formula Column: Escalation Flag

### Your Turn
Type into the Copilot panel:

```
In column N, add a formula that flags each case as "Escalate" or
"OK" based on its Priority and Status:
- "Escalate" if Priority is "Urgent" OR Status is "Escalated"
- "OK" for all other cases
Label the column "Escalation Flag". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(OR(L3="Urgent",M3="Escalated"),"Escalate","OK")
```
Copilot will name the column, write the formula, and fill it down to N27.

---

## Exercise 2 — Add a Formula Column: SLA Breach

### Your Turn
Type into the Copilot panel:

```
In column O, add a formula that checks whether each case breached
its review SLA. Compare the Days in Review in column I against the
Review SLA in column J. If Days in Review is greater than the Review
SLA, return "Breach". Otherwise return "On Time". If Days in Review is
blank (case still open), return "Pending".
Label the column "SLA Breach". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(I3="","Pending",IF(I3>J3,"Breach","On Time"))
```

---

## Exercise 3 — Add a Formula Column: Pending Days

### Your Turn
Type into the Copilot panel:

```
In column P, calculate the number of days each case has been
open. If the case is already resolved (column H has a date), return 0.
If the case is still open, return the number of days since it was
flagged (column G) up to today.
Label the column "Pending Days". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(H3<>"",0,TODAY()-DATEVALUE(G3))
```
Cases with a resolved date show 0. Open cases show how many days they've been waiting for review.

---

## Exercise 4 — Add a Formula Column: Review Category

### Your Turn
Type into the Copilot panel:

```
In column Q, classify each resolved case into a review performance
category based on how the actual Days in Review (column I) compares
to the Review SLA (column J):
- "Fast" if Days in Review is 50% or less of the Review SLA
- "Within SLA" if Days in Review is within the Review SLA
- "Moderate Breach" if Days in Review exceeds SLA by up to 50%
- "Critical Breach" if Days in Review exceeds SLA by more than 50%
- "Pending" if Days in Review is blank
Label the column "Review Category". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=IF(I3="","Pending",IF(I3<=J3*0.5,"Fast",IF(I3<=J3,"Within SLA",IF(I3<=J3*1.5,"Moderate Breach","Critical Breach"))))
```

---

## Exercise 5 — Add a Lookup Column: Escalation Owner (VLOOKUP)

### Your Turn
Type into the Copilot panel:

```
In column R, use VLOOKUP to look up the "Escalation Owner" for each case.
Match the Case Type in column E against the Case Type Reference Table in
columns U–W (Case Type, Standard Review SLA, Escalation Owner), and return
the Escalation Owner from the third column of that table.
Label the column "Escalation Owner (VLOOKUP)". Apply to all 25 rows.
```

### What Copilot Will Produce
```excel
=VLOOKUP(E3,$U$3:$W$7,3,FALSE)
```
- `E3` — the value to look up (this row's Case Type)
- `$U$3:$W$7` — the reference table, locked with `$` so it doesn't shift as the formula fills down
- `3` — return the 3rd column of that table (Escalation Owner)
- `FALSE` — exact match only

> **Try it yourself:** Once filled down, cross-check a few rows — every "Credit Risk Review" case should return **Head - Credit Risk**, every "Fraud Investigation" case should return **Head - Fraud Risk**, and so on.

### 💡 Bonus — Ask Copilot to Pull the SLA Benchmark Too
```
Now add another VLOOKUP in the next empty column that returns the
"Standard Review SLA (Days)" instead — the second column of the same
reference table. Label it "Standard SLA (VLOOKUP)".
```
This shows how the same reference table can drive more than one lookup column, and sets up a natural comparison: does the "Review SLA (Days)" already in column J match the "Standard Review SLA" your VLOOKUP just pulled in? If not, ask Copilot to flag the mismatches — that's a real data-quality check risk teams run before trusting a report.

---

## Exercise 6 — Ask Copilot to Explain a Formula

### Your Turn
Copy the formula from cell **Q3** and paste it into the Copilot panel:

```
Explain this formula to me in simple terms. What does each part do?
```

### What Copilot Will Explain
> *"This formula first checks if Days in Review in I3 is blank — if so, the case is still Pending. Then it checks if Days in Review is at most half the Review SLA, which means the case was reviewed very Fast. Next it checks if Days in Review is within the full Review SLA — that's Within SLA. If the case went over the SLA but not by more than 50%, it's a Moderate Breach. Anything beyond 150% of the Review SLA is a Critical Breach. Each IF only runs when the previous condition wasn't true."*

---

## Exercise 7 — Create a Pivot Table: Cases by Case Type and Status

### Your Turn
Type into the Copilot panel:

```
Create a pivot table that shows the count of cases for each
Case Type, broken down by Status (Closed, Pending, Escalated).
I want to see which case types have the most unresolved or escalated
cases.
```

### What Copilot Will Produce
A new sheet with a Pivot Table:
- **Rows:** Case Type (Credit Risk Review, Fraud Investigation, Collateral Revaluation, Policy Exception Review, Portfolio Watchlist Review)
- **Columns:** Status (Closed, Pending, Escalated)
- **Values:** Count of Case ID

---

## Exercise 8 — Create a Pivot Table: Average Days in Review by Risk Analyst

### Your Turn
Type into the Copilot panel:

```
Now create a pivot table showing the average Days in Review for each
Risk Analyst, broken down by Case Type. I want to identify which
analysts or case types are taking the longest to resolve.
```

### What Copilot Will Produce
- **Rows:** Risk Analyst (Amit Kulkarni, Sunita Rao, Rahul Mehta, Priya Desai, Neha Joshi, Ravi Patil)
- **Columns:** Case Type
- **Values:** Average of Days in Review (TAT)

> **Discussion Point:** Which analyst has the highest average review time on Credit Risk Reviews? Which case type consistently breaches SLA?

---

## Exercise 9 — Bonus: Ask Copilot for Insights

### Your Turn
Type into the Copilot panel:

```
Look at the data in this sheet. Which branches or zones have the most
escalated or SLA-breaching cases? Summarise the key risk areas for the
Risk team in 3 bullet points.
```

### What to Expect
Copilot will scan the data and generate a natural-language summary — no formula needed. This shows how Copilot moves from *calculation* to *analysis* to *insight* within the same Excel session.

---

*Bajaj Finance Limited | AI Academy — Risk Team | Microsoft Copilot Training Programme*
