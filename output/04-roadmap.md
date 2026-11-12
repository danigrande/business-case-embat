# 04 — Roadmap (Now / Next / Later)

> Evidence- and decision-driven roadmap. Durations, thresholds and effort are
> **hypotheses** (there is no baseline for payroll volume outside Embat); they
> are adjusted with the pilot.

## Ordering logic

1. **Validate with clients:** confirm Excel, formats, approvers, deadlines and
   batch-level reconciliation before building more.
2. **MVP on what exists:** import + RBAC + reused approvals, with a real pilot.
3. **Integrations and scale:** native with payroll providers only if demand and
   usage justify it.

## Now / Next / Later table

| Horizon | Question to answer | Objective | What we deliver | Validation milestone |
| ------- | ------------------ | --------- | --------------- | -------------------- |
| **NOW — Validate and capture the first volume**<br>(0–3 months · low-medium effort, hypothesis) | Is it worth building? | Prove that 1–2 clients can run payroll in Embat with control and time savings. | Discovery with the clients who asked; Excel template + validation/preview; RBAC; payroll approvers on the existing engine; batch per entity; send in the country's format (SEPA CT/Bacs); status vs. statement; batch-level reconciliation; payment receipt/export for HR (manual update in v1). | 1–2 pilots live; 100% of their payroll runs in Embat; 0 confidentiality incidents; time per run measured and ≥50% lower than the manual process. |
| **NEXT — Integrate and scale**<br>(3–6 months · medium effort, hypothesis) | Does it solve the problem effectively? | Expand to more clients and reduce manual work with integration. | Native, bidirectional integration with 1 payroll provider (Factorial first: pull payroll + push payment status) if demand justifies it; deadline/cut-off alerts; summary per entity/bank; reconciliation improvements. | 3–5 clients using payroll; ≥50% time saved sustained; ≥99% on-time runs; NRR of pilot clients maintained or growing. |
| **LATER — Expand and monetise**<br>(6–12 months · medium-high effort, hypothesis) | Can we expand the value profitably? | Cover more providers and cases, and evaluate monetisation. | Other payroll providers; advances/bonuses; international payroll (with controls); setup fee per provider connection; volume reporting. | Growth in payment volume per client; adoption in the segment; willingness to pay validated with a setup fee. |

**Effort and opportunity cost:** this sequence competes for capacity with
Payments improvements and connectivity integrations. The final priority depends
on engineering and the rest of the roadmap; gates are **return checkpoints**:
do not scale without demonstrated benefit.

## Go / pivot / kill criteria

- **Go to NEXT if:** 1–2 pilots run 100% of their runs in Embat, with 0
  confidentiality incidents and ≥50% time saved.
- **Go to LATER if:** 3–5 clients use payroll, ≥99% of runs are on time and NRR
  is maintained.
- **Pivot if:** clients demand a native integration from day one or reject
  Excel → prioritise Factorial (C) and delay the rest; or batch-level
  reconciliation is not enough → expand scope.
- **Kill if:** after the pilot clients do not adopt (they keep using the
  portal), time savings do not materialise, or salary-data confidentiality
  cannot be guaranteed.

**What would have to be true to STOP?** That Excel is not acceptable to
clients, that payroll volume does not justify the effort, or that compliance
does not allow operating salary data with the available controls.

## Dependencies that condition the order

- RBAC/confidentiality requirements (Security & Compliance).
- Payroll export formats (Excel/SEPA XML/pain.001, Bacs files) and payment
  formats per bank/country (SEPA CT, Bacs, SWIFT).
- Configurable approval engine (already exists) and client payroll teams.
- Existing bank connectivity (already exists).
- Future Factorial/other API for NEXT (bidirectional: pull payroll + push
  payment status); v1 relies on a receipt/export and manual HR update.
- Customer Success for the pilot and feedback.

## Checklist

- [x] Each horizon has a question to answer and an outcome objective.
- [x] Order respects dependencies: validation → MVP → integration.
- [x] Measurable validation milestones (marked as hypotheses).
- [x] Go / pivot / kill criteria and an explicit stop condition.
- [x] Dates treated as indicative.
- [x] Relative effort per horizon and opportunity cost called out.
