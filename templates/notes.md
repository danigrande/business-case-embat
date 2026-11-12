# Working document — Embat business case (90-min session)

> **One living document.** Capture only what drives decisions.
> Use `/notes` to update it during the session. Separate deliverables are
> generated at the close.

## Context & urgency

- Real case: should Embat invest in expanding Corporate Payments to pay
  salaries?
- Embat: TMS for mid-market and small enterprise groups, multi-entity,
  multi-bank and with an ERP. Modules: Treasury, Cash Reconciliation, Risk and
  Corporate Payments, built on direct bank/ERP connectivity, with AI agents
  inside every module.
- Corporate Payments today: reads outstanding invoices from the ERP, an agent
  groups the payments into a run, a senior person (often the CFO) approves,
  Embat sends them to the bank and checks each payment against the bank
  statement and the ERP.
- Typical clients: Spanish distribution group (6 companies, 4 banks, 400
  employees, ~1,500 supplier invoices/month) and a UK property group (20
  companies, each paying from its own banks).
- Why now? Several clients have already asked for it; the strategy is to
  **increase the number of payments** running through Embat.
- Client request or internal initiative? Client request, aligned with strategy.
- Current pricing: subscription per module + one-time setup fee per bank/ERP
  connection.

## Facts — confirmed information

- Strategy: increase the number of payments in Embat.
- Several clients have asked to pay salaries through Embat.
- Payroll data is **not usually in the ERP**: it usually lives in external
  software such as Factorial.
- Employee expenses already flow through Embat via the ERP's AP module (Embat
  already pays employees for reimbursements).
- Main pain: users already pay suppliers in Embat (banks connected) but have
  to go elsewhere to pay employees.
- Approvals are already configurable; **the people doing payroll are different
  from the people paying vendors**.
- For supplier payments a senior person (often the CFO) approves; **for payroll
  the approver role is not confirmed**.
- For v1 an Excel import is enough, with no HR software integrations (payroll
  runs once a month).
- Salary data is confidential.
- Pricing: subscription per module + setup fee per bank/ERP connection.

## Hypotheses — to validate

- Consolidating all payments in Embat increases stickiness, retention and
  volume (strategy).
- Reusing connectivity + the approval engine makes payroll an incremental
  extension, not a new module.
- The pain is tool-switching and bank-by-bank/entity-by-entity repetition, not
  payroll calculation.
- Batch-level reconciliation is enough (banks aggregate).
- Clients accept a monthly Excel import in v1.
- Including it in Corporate Payments with no extra fee maximises adoption and
  volume; monetising per payroll-provider connection comes later.
- The client's HR system does not need automatic payment-status write-back in
  v1; a manual confirmation or receipt/export is acceptable.
- Confidentiality requires RBAC from day one and is also a selling point.

## Open questions

- Which clients asked for it (size, entities, employees)? How many?
- Factorial only, or other providers (ADP, Sage Payroll…)? What formats do they
  export (Excel, SEPA XML)?
- Who generates the payroll file and who approves payroll (CFO or another
  designated senior approver)? What segregation do they require?
- Deadlines and cadence (monthly, advances, bonuses)? Which banks?
- Which payment format does each bank require for payroll (SEPA CT/pain.001 in
  the eurozone, Bacs in the UK, bank-specific payroll layouts)?
- Does the HR/payroll system need payment-status write-back? Which system, and
  what manual work would it save?
- Is batch-level reconciliation enough, or do they need employee-level detail?
- Would they demand a native integration from day one, or is Excel acceptable?
- Payroll volume outside Embat (employees, runs, amount)?
- Willingness to pay / pricing sensitivity?
- UK: any payroll specifics (RTI, etc.) that should stay out of v1?

## Problem statement (draft)

> Finance teams at multi-entity clients already run supplier payments through
> Embat, but payroll — the largest batch of people payments — still sits
> outside, in bank portals or payroll software. That forces duplicate work bank
> by bank and entity by entity, breaks the consolidated payments view and
> leaves payroll without Embat's traceability and controls. Embat can capture
> that volume by reusing its connectivity and approval engine, with a monthly
> import and confidentiality permissions.

## Outcome target — what would make this a success?

> The client also runs payroll in Embat end to end (import → approval → send →
> reconciliation), increasing payment volume on the platform without adding
> manual work or confidentiality risk. Success = more payments per client, on-
> time payroll and clients consolidating their entire payment cycle in Embat.

## Strategic opportunity / The Bet

> If Embat adds payroll as another flow inside Corporate Payments (Excel import
> + dedicated approvals + RBAC + the existing pipeline), it captures a batch of
> payments that currently goes elsewhere and turns "all your payments in one
> place" into a reason to stay. We bet on **volume and consolidation, not on
> monetising payroll**: every payroll run that comes in is one more payment and
> one more reason not to leave.

## Recommended solution / MVP

- Alternatives considered:
  - A. Do nothing / defer to the payroll provider: loses volume and stickiness;
    the pain persists.
  - B. Excel import + existing pipeline + RBAC and dedicated approvals
    (recommended): fast, reuses capabilities and captures volume.
  - C. Native integration with Factorial/ADP from v1: better UX but requires
    partnership and maintenance; slower.
  - D. Build full payroll (calculation, filings): out of focus.
- Recommended (why): B. 80% of the value is executing the payment where the
  rest already lives; calculation and filings belong to the payroll software.
  It reuses bank connectivity, the approval engine and reconciliation.
- MVP (in / out):
  - In: Excel import (template, validation and preview); employee-to-account/
    entity mapping; batch per entity; dedicated approval flow (four-eyes,
    payroll approvers separate from AP); execution through existing
    connectivity in each country's format (SEPA CT/pain.001 in the eurozone,
    Bacs in the UK); status tracking vs. statement; batch-level reconciliation;
    **payment receipt/export for HR (manual HR update in v1)**; **RBAC for
    confidential data**; audit trail.
  - Out: automatic write-back of payment status to HR software (manual
    receipt/export in v1); native HR software integrations; payroll
    calculation; tax/social security filings; employee-level reconciliation;
    employee portal; international payroll/FX; advances and bonuses; expenses
    (already exist via AP).

## Stakeholders & dependencies

- Teams to involve: Product (Payments), Engineering (payments + connectivity),
  Security & Compliance, Design, Customer Success, client Finance/HR (users and
  approvers).
- Bank/third-party dependencies: payment formats per bank/country (SEPA
  CT/pain.001, Bacs, SWIFT…); payroll software export formats (Excel/SEPA XML
  in the eurozone, Bacs files in the UK); future Factorial/other API.
- Compliance / who validates: Security & Compliance (RBAC, GDPR, retention,
  audit trail for salary data).
- Potential blockers: confidentiality requirements; heterogeneous Excel
  formats; payroll deadlines; bank-aggregated reconciliation.

## Risks

- Confidentiality breach: salaries visible to the wrong people → RBAC and
  audit trail from the start.
- Payroll deadline failure: employees not paid has a higher reputational and
  legal cost than a supplier delay.
- Excel mapping errors (IBAN, amounts, entity) → validation and preview.
- Ambiguous reconciliation: the bank aggregates and may not provide
  employee-level detail.
- Scope creep into payroll calculation/filings (not our job).
- Future dependence on HR providers if native integrations are promised.

## Metrics

- Primary metric (hypothesis): **% of the client's total payment volume
  (suppliers + payroll) executed in Embat**.
- KPIs (2–4):
  - Number of clients adopting payroll and payroll runs executed in Embat.
  - Time saved per run vs. the manual process (bank by bank/entity).
  - % of on-time payroll runs and failed-payment rate.
  - NRR/retention of clients adopting payroll.
- Baseline (or data needed to obtain it): current payment volume per client and
  payroll volume still outside Embat (not measured → open question).

## Roadmap (draft Now / Next / Later)

- NOW: discovery with the clients who asked (confirm Excel, formats, approvers,
  deadlines and batch-level reconciliation); build import + validation + RBAC
  and reuse approvals; pilot with 1–2 clients (Spanish distribution group as
  the multi-entity case).
- NEXT: native, bidirectional integration with 1–2 payroll providers (Factorial
  first: pull payroll + push payment status) if demand justifies it;
  reconciliation improvements; more entities/banks.
- LATER: other providers, advances/bonuses, international payroll; evaluate
  monetisation (setup fee per provider connection).

## Decision log

| Decision | Rationale | Uncertainty |
| -------- | --------- | ----------- |
| Expand Corporate Payments with payroll via Excel import in v1 | Client demand + volume strategy; Excel is enough for a monthly run | Whether clients will demand a native integration from day one |
| Include it in the Payments module with no extra fee in v1 | The strategy is to increase payments; monetising now would slow adoption | Willingness to pay / future monetisation |
| Reuse the approval engine with payroll-specific approvers | It is already configurable; the teams are different | Segregation-of-duties requirements |
| Batch-level reconciliation in v1 | Banks aggregate; employee-level detail is not viable everywhere | Whether clients need employee-level detail |
| RBAC and audit trail from day one | Salary data is confidential; non-negotiable | Exact compliance/GDPR requirements |
| Do not build payroll calculation or filings | It is the payroll software's responsibility, not Embat's | Whether any client expects it from the module |

## Clock

| Phase | Timebox | Start time |
| ----- | ------- | ---------- |
| Problem Discovery | 0–20 | |
| Strategic Fit | 20–30 | |
| Solution & MVP | 30–50 | |
| Metrics | 50–60 | |
| Roadmap | 60–70 | |
| Validation & Risks | 70–80 | |
| Executive Summary | 80–90 | |
