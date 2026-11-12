# 05 — Success Metrics

> There is no baseline for payroll volume outside Embat or for manual time per
> run: targets are **working hypotheses** until the pilot.

## North Star Metric

> **% of the client's total payment volume (suppliers + payroll) executed in
> Embat.**

It reflects customer value (the whole payment cycle in one place, with control
and confidentiality) and is exactly the business strategy: increase the number
of payments running through the platform.

**Rule applied:** we choose the metric that represents value and strategy, not
the easiest one to measure. We do not use "number of imports" as North Star
because it measures activity, not consolidation; the % of volume captured does
change the business and the client experience.

## Product → customer → business value chain

1. **Product:** payroll is imported, approved, executed and reconciled in
   Embat, with confidentiality permissions.
2. **Customer:** stops repeating payroll bank by bank/entity by entity; gains
   control, traceability and on-time execution.
3. **Business:** more payments per client, higher stickiness and retention, and
   a base to monetise payroll-provider connections (causal hypothesis).

## KPIs (3–5)

| KPI | Dimension | Why this one (and not another) | Baseline | Target (hypothesis) |
| --- | --------- | ------------------------------ | -------- | ------------------- |
| **% of client payment volume executed in Embat** | Customer outcome / business | It is the North Star: measures real consolidation, not activity. | None; measure current volume and payroll outside. | +10 pp in the pilot (hypothesis). |
| **Clients adopting payroll and end-to-end runs executed** | Product adoption | Without adoption there is no volume; measures recurring use. | 0 (feature does not exist). | 1–2 pilots in NOW; 3–5 in NEXT. |
| **Time per run vs. manual process** | Operational quality / customer | Time savings are the declared pain (bank-by-bank uploads). | Not measured; estimate with the pilot. | −50% vs. baseline (hypothesis). |
| **% on-time payroll runs and failed-payment rate** | Operational quality | A missed deadline is unacceptable in payroll; guardrail. | None. | ≥99% on time; failed rate ≤ supplier payments. |
| **Confidentiality incidents** | Compliance / trust | Zero tolerance: one unauthorised access breaks trust and the business. | 0. | 0 (hard guardrail). |
| **NRR/retention of clients with payroll** | Business impact | Connects the feature to retention and expansion strategy. | To define with CS data. | Maintain or improve (hypothesis). |

**Consciously discarded:** number of imports (activity), NPS (lagging and noisy
with few clients), attributed revenue (hard to attribute in v1) and gross
"payments processed" (rises with client volume, not with value).

## Leading vs. lagging and perverse effects

- **Leading:** runs imported/validated, time to approval, % of error rows fixed
  before sending.
- **Lagging:** volume captured, on-time runs, NRR.
- **Perverse effects:** pushing volume at the cost of skipping validation;
  hiding confidentiality incidents to keep the metric clean; measuring imports
  rather than resolution. Guardrails: 0 incidents, failed-payment rate and
  mandatory pre-validation.

## Usage vs. impact

- **Usage:** clients importing payroll, runs/month, active payroll users.
- **Impact:** % of volume captured, time saved, on-time rate, NRR.
- **Rule:** high usage with flat volume (they still pay part outside) does not
  justify scaling.

## Measurement plan

### 1. Baseline (during discovery and the first 2 pilot weeks)

- Measure current payment volume per client (suppliers vs. payroll) and manual
  time per run (uploads per entity/bank).
- Identify Excel formats and the number of entities/banks per client.
- **Output:** documented baseline and closed event definitions.

### 2. Pilot (8–12 weeks, hypothesis)

- **Clients:** 1–2 of those who asked; Spanish distribution group as the
  multi-entity case.
- **Instrumentation:** runs imported/executed, time per run, on-time rate,
  validation errors and access logs (audit trail).
- **Design:** pre/post per client; no reliable A/B with so few cases.

### 3. Readout and decision

- **Week 4:** validate flow, permissions and formats.
- **Week 8:** gate (100% runs in Embat, 0 incidents, −50% time).
- **Week 12:** decide NEXT (native integration and more clients) or pivot to
  integration if Excel is not enough. Connected to `output/04-roadmap.md`.

## Open questions (to complete the measurement)

- What is the payroll volume (number of payments and amount) currently outside?
- How much time is spent per run and per entity/bank?
- Who approves and how long does approval take today?
- What error/on-time tolerance do clients require?
- Does the client's HR/payroll system need payment status written back? Which
  system, and what manual work would it save?
- How do we measure retention/expansion for these clients?
- Will clients share time and volume data for the pilot?
