# 06 — Executive Summary

> 2-minute presentation. Conditional recommendation pending validation;
> assumptions marked.

## 1. Problem

Multi-entity clients already pay their suppliers in Embat, but payroll — the
largest batch of people payments — still sits outside, in payroll software and
in each bank's portal, entity by entity. That duplicates work, breaks the
consolidated payments view and leaves payroll without Embat's control and
traceability.

## 2. Why it matters for Embat

The strategy is to increase the number of payments running through the
platform. Several clients have already asked for this. Embat has the bank
connectivity, the approval engine and reconciliation; it already pays employees
for expense reimbursements via AP. Payroll is the missing batch to close the
payments cycle.

## 3. Opportunity — The Bet

If we add payroll as another flow inside Corporate Payments (monthly Excel
import + dedicated approvers + confidentiality permissions on the existing
pipeline), we capture volume that currently goes elsewhere and turn "all your
payments in one place" into a reason to stay. We bet on **volume and
consolidation, not on monetising payroll**.

## 4. Recommended solution

**Excel import + existing payments pipeline + RBAC + payroll approvers.** We
discard doing nothing (loses volume and stickiness), native integration from v1
(partnership and maintenance; better in NEXT) and building full payroll
(calculation and filings belong to the payroll provider). The trade-off is a
manual monthly import in exchange for time-to-value and a low build.

**Condition:** if clients reject Excel or demand a native integration from day
one, pivot to Factorial as the first integration.

## 5. MVP — included and excluded

- **Included:** Excel import with validation/preview; employee-to-entity
  mapping; batch per entity; four-eyes approval with payroll approvers; send in
  the country's format (SEPA CT/Bacs) through existing connectivity; status vs.
  statement; batch-level reconciliation; payment receipt/export for HR (manual
  update in v1); RBAC and audit trail.
- **Excluded:** native HR integrations, automatic write-back to HR software,
  payroll calculation, tax/SS filings, employee-level reconciliation, employee
  portal, international payroll/FX, advances and bonuses.

## 6. Main risks

- **Salary confidentiality:** RBAC by role/entity and audit trail from day one;
  no launch without it.
- **Payroll deadline:** failing leaves employees unpaid → alerts, cut-offs and
  clear statuses.
- **Heterogeneous Excel/mapping errors:** standard template, validation and
  preview before sending.
- **Bank-aggregated reconciliation:** v1 at batch level; validate whether that
  is enough.

## 7. Success metrics

- **North Star:** % of the client's total payment volume (suppliers + payroll)
  executed in Embat.
- **KPIs:** clients/runs adopted; −50% time per run; ≥99% on-time runs; **0
  confidentiality incidents**; NRR maintained. No baseline for payroll outside:
  measure it in the pilot.

## 8. Next steps and decision requested

1. Discovery with the clients who asked: volume, formats, approvers, deadlines,
   whether batch-level reconciliation is enough and whether HR needs payment
   status written back.
2. Build import + validation + RBAC and configure payroll approvers; reuse the
   pipeline and connectivity.
3. Pilot with 1–2 clients (Spanish distribution group as the multi-entity
   case).
4. Gate at week 8: 100% runs in Embat, 0 incidents and −50% time → scale; if
   not, pivot to native integration.
5. **Decision requested:** approve the pilot and the limited build of the
   payroll import, keeping it inside Corporate Payments with no extra fee in
   v1.

**Capacity note:** low-medium effort in NOW (reuses the pipeline); it competes
with Payments and connectivity improvements. If there is a higher priority, the
order changes.

## 9. Open questions & assumptions

- **Facts:** volume strategy; several clients ask for it; payroll outside the
  ERP (Factorial); employee expenses already in Embat; configurable approvals
  with separate teams; Excel enough for v1; confidential data.
- **Hypotheses:** consolidating payments increases stickiness; Excel is enough;
  batch-level reconciliation is sufficient; including it with no extra fee
  maximises adoption.
- **Open questions:** clients and size; providers/formats; approvers and
  segregation; deadlines and banks; volume outside Embat; willingness to pay;
  HR payment-status write-back.

## Closing

> "What I recommend is bringing payroll into the payments pipeline that already
> works: Excel import, dedicated approvers and confidentiality permissions. The
> trade-off is a manual monthly import in v1; we accept it because it captures
> volume now, reuses what is built and leaves native integration for when
> demand justifies it."
