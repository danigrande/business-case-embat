# 02 — Problem Statement

> Provisional document. Demand and pain are confirmed by Alex; the payroll
> volume outside Embat, willingness to pay and reconciliation requirements are
> still open (open questions).

## Problem statement (level 3) — EN

> Finance teams at multi-entity clients already run supplier payments through
> Embat, but payroll — the largest batch of people payments — still sits
> outside, in bank portals or payroll software. That forces duplicate work bank
> by bank and entity by entity, breaks the consolidated payments view and
> leaves payroll without Embat's traceability and controls.

**Confidence: medium-high.** Demand, pain and Excel-import feasibility are
confirmed; the size of the volume, reconciliation requirements and willingness
to pay are not.

## One-liner (to verbalise)

> "Clients already pay suppliers in Embat; payroll is the biggest batch still
> outside, and it costs them duplicate work and control."

## Level 1 — Problem framing

| Field | Answer |
| ----- | ------ |
| **Affected user** | Finance team paying suppliers in Embat; payroll/HR team preparing payroll. |
| **Buyer / decision-maker** | CFO (hypothesis; validate with the clients who asked). |
| **Other stakeholders** | Client HR/payroll, Security & Compliance, Customer Success. |
| **Context** | Mid-market/small enterprise, multi-entity and multi-bank. Examples: Spanish distribution group (6 companies, 4 banks, 400 employees, ~1,500 invoices/month); UK property group (20 companies). |
| **Task / As-Is workflow** | Suppliers: ERP → agent groups invoices → CFO approves → Embat sends and reconciles. Payroll: payroll software (e.g. Factorial) → export → each bank's portal, entity by entity. |
| **Workaround** | Bank portals bank by bank/entity by entity; payroll files uploaded manually; Excel. |
| **Observed friction** | Duplicate work, tool-switching, incomplete payments view, payroll without Embat's four-eyes/audit trail. |
| **Frequency & severity** | Monthly payroll (12 runs/year per client); hard deadline and high cost if it fails. |
| **Desired outcome** | Run payroll in Embat end to end, with control and confidentiality. |

## Level 2 — Evidence

- **What we know:** strategy = increase the number of payments; several clients
  have asked; payroll data is not in the ERP (external software such as
  Factorial); employee expenses already flow through Embat via AP; approvals
  are configurable and payroll teams are different; Excel is enough for v1
  (monthly run); salary data is confidential.
- **What is missing:** how many clients and of what size; payroll volume
  outside Embat; export formats; who approves and with what segregation;
  whether batch-level reconciliation is enough; willingness to pay.
- **Root cause:** the payments pipeline already exists and works, but the
  payroll source (HR software) and its requirements (confidentiality, different
  approvers, deadline) sit outside the platform. High confidence in the
  diagnosis; volume still unquantified.

## Facts / Hypotheses / Open questions

### Facts (confirmed)

- Strategy: increase the number of payments in Embat.
- Several clients have asked to pay salaries.
- Payroll is not in the ERP; it lives in external software such as Factorial.
- Employee expenses are already paid through Embat (via AP).
- Pain: they pay suppliers in Embat but payroll goes elsewhere.
- Approvals are configurable; payroll teams are different from AP.
- Excel is enough for v1; no HR integrations; monthly frequency.
- Salary data is confidential.
- Pricing: subscription per module + setup fee per bank/ERP connection.

### Hypotheses (to validate)

- Consolidating all payments increases stickiness, retention and volume.
- Reusing connectivity + approvals makes payroll incremental (low build).
- The pain is tool-switching and multi-entity repetition, not payroll
  calculation.
- Batch-level reconciliation is enough.
- Clients accept Excel in v1.
- Including it in Payments with no extra fee maximises adoption; monetising per
  provider connection comes later.
- Confidentiality requires RBAC from day one and is a selling point.

### Open questions

- Which clients asked (size, entities, employees)? How many?
- Factorial only, or other providers? What do they export (Excel, SEPA XML/pain.001, Bacs files)?
- Who generates the payroll file and who approves? What segregation do they
  require?
- Deadlines/cadence (monthly, advances, bonuses)? Which banks?
- Is batch-level reconciliation enough, or do they need employee-level detail?
- Will they demand a native integration from day one?
- Payroll volume outside Embat and willingness to pay?
- UK: any specifics (RTI, etc.) that stay out of v1?

## Quantified impact

- **Fact:** there is no measurement of the payroll volume that sits outside
  Embat.
- **Hypothesis (to validate):** the cost is the time spent uploading payroll
  bank by bank/entity + error/deadline risk + loss of control and stickiness.
- **Illustrative example (hypothesis, not data):** 6 entities × 4 banks = 24
  uploads/month; 15–30 min each → 6–12 h/month per client, plus manual error
  risk. Replace with the real baseline.

## Quality checklist

- [x] Specific (user, task, context), not generic.
- [x] Separates symptom (payroll outside) from cause (HR source + requirements
      outside the pipeline).
- [x] Impact scoped; quantification pending (marked as hypothesis).
- [x] No solution yet.
- [x] Identifies what is missing and which question would resolve it.
