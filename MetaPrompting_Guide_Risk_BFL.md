# Meta-Prompting Guide — Risk Team
**Microsoft Copilot Training | Bajaj Finance Limited**

---

## What Is Meta-Prompting?

Instead of writing a prompt yourself, you ask Copilot to write the prompt for you — by telling it your role, your task, and what you need.

You are essentially saying:

> *"You are a prompt expert. You know how to talk to AI. Write me a prompt I can use for my actual risk work."*

The output becomes your **reference prompt** — something you refine and reuse across credit portfolio reviews, fraud pattern checks, risk reporting, policy and compliance review, and portfolio monitoring workflows.

---

## The Core Meta-Prompt Formula

```
Act as a Microsoft Copilot prompt expert.
I am a [YOUR ROLE] at [COMPANY/CONTEXT].
I need to [WHAT YOU WANT TO DO].
My audience is [WHO WILL READ THE OUTPUT].
Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, output format, and tone.
```

---

## Meta-Prompts for Risk Team — Bajaj Finance

Use these as your starting point. Copy, paste, and run in Copilot. Use the output as your working prompt for your exercises.

---

### 1. Credit Portfolio Risk Analysis

```
Act as a Microsoft Copilot prompt expert.
I am a Credit Risk Analyst at Bajaj Finance Limited. I am responsible for tracking
loan portfolio health across business units including MSME Lending, Consumer Lending,
Housing Finance, and Rural Lending. I maintain a Loan Portfolio Risk Register in Excel
with fields including: Loan ID, Product, Business Unit, Region, Disbursed Amount,
Outstanding Amount, DPD (Days Past Due), Risk Grade (A-E), Credit Score, Collateral
Coverage %, LTV %, and Account Status.

I need to identify total outstanding and Gross NPA % by business unit, flag all loans
with Risk Grade D or E, highlight accounts in SMA-1/SMA-2 that are trending toward NPA,
and surface any concentration risk by product or region.

My audience is the Head - Credit Risk, for the monthly portfolio risk review.

Write me a detailed, structured Copilot prompt I can use to produce this analysis from
my attached Excel register. The prompt should specify format (business-unit summary
table — Business Unit | Total Outstanding | Gross NPA % | SMA-1/SMA-2 Count | Risk Grade
D/E Count + a risk commentary line per business unit), tone (formal, data-led, review-
ready), and what to surface (Risk Grade D or E, Account Status = SMA-1, SMA-2 or NPA,
DPD above 60 days).
```

---

### 2. Fraud Pattern Identification

```
Act as a Microsoft Copilot prompt expert.
I am a Fraud Risk Analyst at Bajaj Finance Limited. I review transaction and alert
data ahead of the Fraud Monitoring Group meeting. I maintain a Fraud Transaction
Alerts log in Excel with fields including: Alert ID, Customer ID, Txn Date, Txn Type,
Channel, Amount, Location, Device Change Flag, Velocity Flag, Geo-Mismatch Flag,
Anomaly Score (0-100), Alert Status, and Assigned Analyst.

I need to identify patterns across alerts with high anomaly scores (above 75), alerts
flagged with both Velocity and Geo-Mismatch, and any customer, location, or channel
appearing more than once among escalated alerts. I also need a recommended action for
each pattern found.

My audience is the Head - Fraud Risk, ahead of the Fraud Monitoring Group review.

Write me a detailed, structured Copilot prompt I can use to produce this Fraud Pattern
Brief from my attached Excel log. The prompt should specify format (pattern summary
table — Pattern | Alerts Involved | Common Attribute | Recommended Action + a short
narrative brief of no more than 200 words), tone (investigative, precise, no
speculation beyond what the data supports), and what to surface (Anomaly Score above
75, Alert Status = Escalated - Fraud or Under Review, repeated Customer ID/Location/
Channel across alerts).
```

---

### 3. Risk Reporting

```
Act as a Microsoft Copilot prompt expert.
I am a Risk Reporting Manager at Bajaj Finance Limited. I prepare monthly risk
indicator packs for the Chief Risk Officer and Board Risk Committee. I maintain a
Risk Indicator Dashboard in Excel with fields including: Month, Business Unit, Gross
NPA %, Net NPA %, PAR-30 %, PAR-60 %, PAR-90 %, Fresh Slippage (₹ Cr), Restructured
Book (₹ Cr), Provision Coverage Ratio %, Credit Cost %, Target GNPA %, and Commentary.

I need to summarise Gross NPA%, Net NPA%, PAR-30/60/90, Provision Coverage Ratio and
Credit Cost trends from April to June 2026 by business unit, flag any business unit
where Gross NPA% has exceeded its Target GNPA% for two consecutive months, and produce
a RAG (Red/Amber/Green) status per business unit using the commentary as supporting
context.

My audience is the Chief Risk Officer, for the Board Risk Committee pack.

Write me a detailed, structured Copilot prompt I can use to produce this Risk
Indicator Report from my attached Excel tracker. The prompt should specify format
(executive summary — 3-4 lines + RAG status table: Business Unit | Gross NPA % |
Target GNPA % | Status | Trend + one-line commentary per Red/Amber unit), tone
(executive-level, concise, Board-ready — 350 words maximum), and what to surface
(Gross NPA% above Target GNPA% for 2+ consecutive months, Provision Coverage Ratio
below 70%, Credit Cost trending upward).
```

---

### 4. Policy and Compliance Review

```
Act as a Microsoft Copilot prompt expert.
I am a Risk & Compliance Officer at Bajaj Finance Limited. I track risk policy
currency and compliance gaps ahead of Internal Audit reviews. I maintain a Policy
Compliance Tracker in Excel with fields including: Policy ID, Policy Name, Regulatory
Reference, Version, Last Review Date, Next Review Due, Key Compliance Requirement,
Policy Owner, Compliance Status, and Risk Rating.

I need to list all policies with Compliance Status "Gap Identified" or "In Progress",
sorted by Next Review Due with the earliest first, summarise the Key Compliance
Requirement for each in one line, and suggest a priority order for remediation based
on Risk Rating.

My audience is the Chief Risk Officer, ahead of the Internal Audit review.

Write me a detailed, structured Copilot prompt I can use to produce this Policy
Compliance Brief from my attached Excel tracker. The prompt should specify format
(remediation priority table — Priority Rank | Policy Name | Risk Rating | Compliance
Status | Next Review Due | One-Line Requirement + a short cover note flagging High-
risk gaps first), tone (formal, audit-ready, precise references to regulatory
source), and what to surface (Compliance Status = Gap Identified or In Progress,
Risk Rating = High, Next Review Due within 90 days).
```

---

### 5. Risk Monitoring

```
Act as a Microsoft Copilot prompt expert.
I am a Portfolio Monitoring Analyst at Bajaj Finance Limited. I track portfolio
performance and emerging risk signals for the Chief Risk Officer and Business Unit
Heads. I maintain a Portfolio Monitoring Trend sheet in Excel with fields including:
Month, Business Unit, Total AUM (₹ Cr), Disbursement (₹ Cr), Collection Efficiency %,
30+ DPD %, Early Warning Signals (Count), and Top Early Warning Signal.

I need to identify which business units show a worsening trend in Collection
Efficiency % and 30+ DPD % from April to June 2026, count the Early Warning Signals
per business unit, summarise the Top Early Warning Signal text for each, and rank
business units from highest to lowest emerging risk.

My audience is the Chief Risk Officer and respective Business Unit Heads.

Write me a detailed, structured Copilot prompt I can use to produce this Risk
Monitoring Brief from my attached Excel tracker. The prompt should specify format
(risk ranking table — Rank | Business Unit | Collection Efficiency Trend | 30+ DPD
Trend | Early Warning Count | Top Signal + a one-paragraph early-warning narrative for
the highest-risk unit), tone (early-warning focused, direct, action-oriented), and
what to surface (Collection Efficiency % declining month-on-month, 30+ DPD % rising
month-on-month, Early Warning Signals count of 5 or more).
```

---

## Still Confused? Run This.

If the prompt Copilot wrote doesn't feel right — too generic, wrong format, wrong tone — don't rewrite it yourself. Use this follow-up prompt instead:

```
The prompt you wrote is a good start, but I need you to adjust it.
Here is what I want to change:

- [Describe what felt off — e.g., "the format doesn't match what our Chief Risk
  Officer expects in a Board Risk Committee pack"]
- [Describe what's missing — e.g., "it doesn't tell Copilot to flag business units
  where Gross NPA% has crossed Target GNPA% for two months running"]
- [Describe the tone issue — e.g., "it sounds too casual for an Internal Audit
  review"]

Please rewrite the prompt with these corrections.
Keep the same structure (Role / Task / Context / Format / Tone) but fix the parts
I've described.
```

---

## What to Do With the Output

Once Copilot gives you a well-structured prompt:

1. **Read it** — does it reflect your actual Risk role and the kind of work you handle at BFL?
2. **Replace the placeholders** — swap generic text with your real reporting period, business unit, policy area, or risk threshold.
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
