# 03 — Solution & MVP

> Recommendation pending validation. Based on the Facts and Hypotheses in
> `templates/notes.md`; assumptions are marked.

## 0. Value hypothesis

- **Behaviour to change:** the client runs payroll in Embat instead of going to
  the bank portal or the payroll software.
- **Expected outcome:** more payments per client, on-time payroll and the whole
  payment cycle in one platform (control + confidentiality).
- **Why we believe it will work:** the payments pipeline, connectivity and
  approvals already exist; only the source (Excel) and permissions are missing.
- **Evidence:** several clients ask for it; volume strategy; employee expenses
  are already paid through Embat. Volume and willingness to pay still need to
  be quantified.

## 1. Build vs. buy vs. improve (before deciding to build)

| Option | Assessment |
| ------ | ---------- |
| **Improve** | Reuse Corporate Payments, bank connectivity, approval engine and reconciliation. That is 80% of the product. |
| **Process** | An Excel template + validation reduces errors, but does not solve consolidation or control. |
| **Buy / integrate** | Native Factorial/ADP integration: better UX, but partnership and per-provider maintenance; not for v1. |
| **Build** | Excel import + RBAC + payroll approver configuration on top of the existing pipeline. |

**Decision:** improve + limited build. Do not build payroll calculation or
filings: that belongs to the payroll software, not Embat.

## 1.1 Technical feasibility and operational economics (cross-cutting)

- **Technical feasibility:** high; the pipeline and connectivity are reused.
  New work is import/validation, RBAC and approver configuration.
- **Payroll/ERP/bank dependencies:** Excel format per provider; payment files
  per bank/country (SEPA CT/pain.001, Bacs, SWIFT); future Factorial/other API.
- **Operational cost:** low (one run/month per client); support for Excel
  mappings and formats.
- **Reliability:** payroll deadline; pre-validation and clear statuses; never
  retry blindly.
- **Relative MVP effort: low-medium (hypothesis, to validate with engineering).**
  The hardest part is RBAC/confidentiality and format validation, not sending.
- **Security and auditability:** salary data is confidential; permissions by
  role/entity and audit trail from the design.
- **AI:** not the core of this feature; an agent could later help map or
  validate the Excel, but not in v1.

## 2. To-Be workflow (5–8 steps)

| # | Step | Automatic / Human |
| - | ---- | ----------------- |
| 1 | The payroll team exports payroll to Excel from its HR software. | Human (outside Embat) |
| 2 | Import into Embat with a template, validation (IBAN, amounts, entity) and preview. | Automatic |
| 3 | Map employees to accounts and entities; fix invalid rows. | Human (assisted) |
| 4 | Create the batch per entity with an amount/bank summary. | Automatic |
| 5 | Four-eyes approval: payroll/HR prepares and a designated senior approver approves (separate from AP; role to confirm). | Human |
| 6 | Send through existing bank connectivity in the country's format (SEPA CT/pain.001 in the eurozone; Bacs in the UK). | Automatic |
| 7 | Track status vs. statement; alert on rejection or deadline risk. | Automatic |
| 8 | Batch-level reconciliation, auditable record and payment receipt/export for finance/HR; HR system update is manual in v1. | Automatic + human |

> **HR system update:** Embat does not write payment status back to the HR
> software in v1. After reconciliation it provides a batch receipt/export; the
> client updates its HR records manually if needed. Bidirectional write-back is
> a NEXT integration (Factorial first).

**Fallback:** if the Excel is invalid, rows are flagged and not sent; if the
bank does not confirm, the payment stays "status unconfirmed" and is not retried
without validation. Missing data is never hidden.

## 3. Solution alternatives

| Alternative | One-line description | Value | Cost/Complexity | Risk |
| ----------- | -------------------- | ----- | --------------- | ---- |
| A. Do nothing / defer | Leave payroll outside Embat. | Low: loses volume and stickiness; pain persists. | Low. | High: volume strategy missed. |
| B. Excel import + pipeline + RBAC | Payroll as a Payments flow with import, dedicated approvers and permissions. | High: captures volume with low build. | Low-medium. | Medium: formats and confidentiality. |
| C. Native integration from v1 | API with Factorial/ADP to pull payroll automatically. | High future value; better UX. | Medium-high: partnership and maintenance. | Medium: provider dependency. |
| D. Build full payroll | Calculation, filings and payments. | Low for Embat: out of focus. | High. | High: not our business. |

**Recommended: B.** Captures volume with minimal build, reuses connectivity and
approvals and leaves native integration for NEXT if demand justifies it. A does
not meet the strategy; C is premature; D is another product.

**What evidence would change the recommendation:** if clients demand a native
integration from day one or reject Excel, pivot to C (starting with Factorial);
if batch-level reconciliation is not enough, expand the scope.

## 4. MVP — MoSCoW and learning

| Must have | Should have | Could have | Won't have (now) |
| --------- | ----------- | ---------- | ---------------- |
| Excel import with template, validation and preview. | Templates per bank/entity. | Advanced IBAN validation. | Native HR software integrations. |
| Employee-to-account/entity mapping. | Summary per entity/bank. | Evidence export. | Payroll calculation and tax/SS filings. |
| Batch per entity with summary. | Deadline and cut-off alerts. | Run history. | Employee-level reconciliation. |
| Four-eyes approval with payroll approvers (separate from AP). | | | Employee portal. |
| Execution through existing connectivity in the country's format (SEPA CT, Bacs…). | | | International payroll / FX. |
| Status vs. statement and batch-level reconciliation. | | | Advances and bonuses. |
| RBAC and audit trail (confidential salary data). | Payment receipt/export for HR records. | | Automatic write-back to HR software (native integration, NEXT). |

> "Won't" means **out because of capacity, risk or sequencing**, not lack of
> value.

**Pilot segment:** 1–2 of the clients who asked; ideally the Spanish
distribution group (6 companies, 4 banks, 400 employees) as the most
representative multi-entity case. The UK group validates multi-entity; UK
payroll specifics (RTI) stay out of v1.

**Learning-oriented MVP:**

| Element | Answer |
| ------- | ------ |
| Pilot user | Payroll/HR team + designated approver of 1–2 clients (role to confirm). |
| Hypothesis | Excel + the existing pipeline is enough to run payroll with control and time savings. |
| Minimum experience | Import, validate, approve and send payroll from Embat with restricted permissions. |
| Learning | Whether Excel is acceptable, whether batch-level reconciliation is enough and how much time is saved. |
| Success criterion | 100% of pilot runs in Embat, 0 confidentiality incidents and ≥50% time saved per run. |

## 4.1 Adoption and trust

- Integrate payroll into the Payments module, not as a separate product.
- The user keeps control: import and validation are assisted; the approver
  decides the send.
- Explain clearly which employees and entities are in each batch.
- Full traceability (who imported, who approved, when, what changed).
- **Visible confidentiality:** access restricted by role/entity; the AP team
  does not see salaries.
- Make the manual HR update explicit: provide a receipt/export so the client's
  step is simple.
- Handle the no-data case: invalid rows flagged, no silent partial sends.

## 5. Acceptance criteria

- **Given** a payroll Excel file, **when** it is imported, **then** it is
  validated (IBAN, amounts, entity) and a preview shows flagged errors.
- **Given** a file with invalid rows, **when** it is validated, **then** those
  rows are not sent and the user can fix them before continuing.
- **Given** a payroll batch, **when** it is sent for approval, **then** only the
  configured payroll approvers can see and approve it.
- **Given** an approved batch, **when** it is executed, **then** it is sent through
  the corresponding bank connectivity in the country's format (e.g. SEPA CT in
  the eurozone, Bacs in the UK) and recorded.
- **Given** an executed payment, **when** the statement arrives, **then** its
  status is updated and it is reconciled at batch level.
- **Given** a user without the payroll role, **when** they try to view the
  batch, **then** access is denied and logged in the audit trail.

## 6. Dependencies, risks and failure scenarios

| Type | Dependency/Risk | Mitigation |
| ---- | --------------- | ---------- |
| Technical | Heterogeneous Excel formats per client/provider. | Standard template + configurable mapping + validation. |
| Technical | RBAC and entity permissions may not exist or be sufficient. | Security review; permissions from day one; do not launch without them. |
| Data | Wrong employee IBANs/accounts. | Validation and preview before sending. |
| Compliance/security | Salary confidentiality (GDPR). | Role/entity-restricted access, immutable logs and defined retention. |
| Operational | Payroll deadline and bank cut-offs. | Alerts, calendar and clear statuses; test with the pilot. |
| Technical | HR system update is manual in v1; write-back needs a provider API. | Provide a receipt/export; bidirectional integration in NEXT (Factorial). |
| Business | Expectation of a native integration from day one. | Communicate Excel in v1 and the integration roadmap. |

**Failure scenarios:**

- **Invalid Excel:** rows flagged, preview and send blocked until fixed; never a
  silent partial send.
- **Bank does not respond or timeout:** "status unconfirmed"; no retry without
  validation (avoid duplicate payment).
- **Deadline at risk:** early alert to the approver and the run owner.
- **Unauthorised access:** denial + audit-trail record; permission review.
- **Mapping error (employee to account):** validation and explicit confirmation
  in the preview.

## 7. Explicit out-of-scope

- Native HR software integrations (Factorial/ADP) in v1.
- Payroll calculation, withholdings and tax/social security filings.
- Employee-level reconciliation (v1 is batch-level).
- Employee portal and self-service.
- International payroll and FX.
- Advances, bonuses and extraordinary settlements.
- Employee expenses (already covered via AP).
- Automatic write-back of payment status to HR software.
- Pricing model changes.

## Phrase to use

> "I would rather deliver a smaller solution that solves the core customer
> problem reliably than a broader solution that introduces unnecessary
> complexity."
