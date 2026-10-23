# M365 Copilot Prompt Guide — Risk Team
## 5 Workplace Use Cases
**Bajaj Finance Limited | AI Academy — Risk | FY 2026-27**
**Tool: M365 Copilot Chat (microsoft365.com/chat)**

---

## How to Use This Guide

This guide gives you ready-to-use prompts for five real Risk team tasks. Each use case follows a simple two-step approach:

**Step 1 — Generate your prompt** using the Meta Prompt Framework
**Step 2 — Apply it live** by attaching your Excel file and running the generated prompt

You don't need to write prompts from scratch. The Meta Prompt does that for you.

---

## Use Case 1 — Credit Portfolio Risk Analysis

**Meta Prompt**
```
Act as a Microsoft Copilot prompt expert.
I am a Credit Risk Analyst at Bajaj Finance Limited.
I need to analyse our loan portfolio to identify risk exposure and performance trends across business units, risk grades and DPD buckets.
My audience is the Head - Credit Risk, for the monthly portfolio risk review.
Write me the best possible prompt to get this done.
```

**Generated Working Prompt (example)**
```
Using the Loan Portfolio Risk Register sheet, analyse the loan portfolio by business unit and risk grade.
Identify: (1) total outstanding and Gross NPA % by business unit, (2) loans with Risk Grade D or E and their DPD,
(3) accounts in SMA-1/SMA-2 that are trending toward NPA, (4) any concentration risk by product or region.
Present as a structured summary with a risk commentary line per business unit, suitable for the Head - Credit Risk.
```

💡 **Try It Yourself:** Attach `Loan Portfolio Risk Register` with `/`, run the prompt, and compare Copilot's Gross NPA % against the Portfolio Summary block already on the sheet.

---

## Use Case 2 — Fraud Pattern Identification

**Meta Prompt**
```
Act as a Microsoft Copilot prompt expert.
I am a Fraud Risk Analyst at Bajaj Finance Limited.
I need to review transaction and alert patterns to detect potential anomalies or suspicious behaviour that may indicate fraud.
My audience is the Head - Fraud Risk, ahead of the Fraud Monitoring Group review.
Write me the best possible prompt to get this done.
```

**Generated Working Prompt (example)**
```
Using the Fraud Transaction Alerts sheet, identify patterns across alerts with high anomaly scores (above 75),
alerts flagged with both Velocity and Geo-Mismatch, and alerts assigned to each analyst.
Group findings by Transaction Type and Channel. Highlight any customer, location or channel appearing more than once
in escalated alerts. Present as a short brief with a recommended action for each pattern, for the Fraud Monitoring Group.
```

💡 **Try It Yourself:** Attach `Fraud Transaction Alerts` with `/`, run the prompt, and check the "Escalated - Fraud" count Copilot finds against the Alert Summary block on the sheet.

---

## Use Case 3 — Risk Reporting

**Meta Prompt**
```
Act as a Microsoft Copilot prompt expert.
I am a Risk Reporting Manager at Bajaj Finance Limited.
I need to prepare a structured summary of key risk indicators for management review, covering trends across business units.
My audience is the Chief Risk Officer, for the Board Risk Committee pack.
Write me the best possible prompt to get this done.
```

**Generated Working Prompt (example)**
```
Using the Risk Indicator Dashboard sheet, summarise Gross NPA%, Net NPA%, PAR-30/60/90, Provision Coverage Ratio
and Credit Cost trends from April to June 2026, by business unit. Flag any business unit where Gross NPA% has
exceeded its Target GNPA% for two consecutive months. Include the commentary notes as supporting context.
Present as an executive summary with a RAG (Red/Amber/Green) status per business unit, for the Board Risk Committee.
```

💡 **Try It Yourself:** Attach `Risk Indicator Dashboard` with `/`, run the prompt, and see which business units Copilot marks Red or Amber.

---

## Use Case 4 — Policy and Compliance Review

**Meta Prompt**
```
Act as a Microsoft Copilot prompt expert.
I am a Risk & Compliance Officer at Bajaj Finance Limited.
I need to analyse our risk policy documents and identify key compliance requirements, gaps and upcoming review deadlines.
My audience is the Chief Risk Officer, ahead of the Internal Audit review.
Write me the best possible prompt to get this done.
```

**Generated Working Prompt (example)**
```
Using the Policy Compliance Tracker sheet, list all policies with Compliance Status "Gap Identified" or "In Progress",
along with their Risk Rating, Owner and Next Review Due date. Sort by Next Review Due (earliest first).
For each, summarise the Key Compliance Requirement in one line and suggest a priority order for remediation
based on Risk Rating, for the Chief Risk Officer ahead of Internal Audit.
```

💡 **Try It Yourself:** Attach `Policy Compliance Tracker` with `/`, run the prompt, and check whether Copilot correctly cites the Regulatory Reference for each policy rather than generic language.

---

## Use Case 5 — Risk Monitoring

**Meta Prompt**
```
Act as a Microsoft Copilot prompt expert.
I am a Portfolio Monitoring Analyst at Bajaj Finance Limited.
I need to track portfolio performance month-on-month and identify emerging risk signals before they become losses.
My audience is the Chief Risk Officer and respective Business Unit Heads.
Write me the best possible prompt to get this done.
```

**Generated Working Prompt (example)**
```
Using the Portfolio Monitoring Trend sheet, identify which business units show a worsening trend in
Collection Efficiency % and 30+ DPD % from April to June 2026. Count the Early Warning Signals per business unit
and summarise the Top Early Warning Signal text for each. Rank business units from highest to lowest emerging risk,
and present as an early-warning brief for the Chief Risk Officer and Business Unit Heads.
```

💡 **Try It Yourself:** Attach `Portfolio Monitoring Trend` with `/`, run the prompt, and note which business unit comes out highest-risk — then compare it with what you found in Use Case 1 and 3.

---

## RTCFT Quick Reference Card

| Element | Meaning | Example |
|---|---|---|
| **R** — Role | Who Copilot should act as | "Act as a Microsoft Copilot prompt expert" |
| **T** — Task | What you need done | "Analyse loan portfolio for risk exposure" |
| **C** — Context | Your role + company context | "I am a Credit Risk Analyst at Bajaj Finance Limited" |
| **F** — Format | Structure of the output | "Present as a structured summary with RAG status" |
| **T** — Tone | Audience-appropriate tone | "For the Board Risk Committee" (formal, concise) |

---

## Still Confused? Try These Follow-Ups

| If your output is... | Try asking... |
|---|---|
| Too generic | "Make this specific to the MSME Lending and Rural Lending business units only." |
| Too long for a Board pack | "Summarise this in 5 bullet points, no more than 15 words each." |
| Not in the format you need | "Present this as a table with columns: Business Unit, Metric, Current, Target, Status." |

---

## What to Do With the Output

Once Copilot gives you a well-structured prompt:

1. **Read it** — does it reflect your actual Risk role and the kind of work you handle at BFL?
2. **Replace the placeholders** — swap in your real reporting period, business unit, policy area, or risk threshold.
3. **Run it** — use it on the exercise dataset (`BFL_Risk_Copilot_Training_Dataset.xlsx`) provided during training.
4. **Save it** — this is your reusable reference prompt for that risk task type.

---

## 📋 Risk Team Quick Reference

| Use Case | Sheet in Dataset | Key Fields Copilot Will Use |
|---|---|---|
| Credit Portfolio Risk Analysis | Loan Portfolio Risk Register | Risk Grade, DPD, Outstanding Amount, Account Status |
| Fraud Pattern Identification | Fraud Transaction Alerts | Anomaly Score, Velocity/Geo-Mismatch Flags, Alert Status |
| Risk Reporting | Risk Indicator Dashboard | Gross/Net NPA %, PAR buckets, PCR, Target GNPA % |
| Policy and Compliance Review | Policy Compliance Tracker | Compliance Status, Risk Rating, Next Review Due |
| Risk Monitoring | Portfolio Monitoring Trend | Collection Efficiency %, 30+ DPD %, Early Warning Signals |

---

*Bajaj Finance Limited | AI Academy — Risk Team | Microsoft Copilot Training Programme*
*This guide is for participant use. Please do not share outside your organisation.*
