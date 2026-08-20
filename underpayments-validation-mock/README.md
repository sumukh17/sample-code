# Underpayments Validation — Mock Screens

A clickable, front-end-only prototype for validating hospital claim underpayments
against a sample payer contract. Expected-vs-actual reconciliation with per-finding
explainability. **No backend** — all data and validation logic run in the page.

## Run it

Just open `index.html` in any modern browser — double-click it, or:

```
start index.html      # Windows
```

No build step, no server, no internet connection. Everything (styles, scripts,
sample contract, and sample accounts) is inlined in the single file.

## Screens

- **Worklist** — accounts flagged for review, with KPIs, filters, and a
  Discharge / Charges / Expected / Paid / Variance / Finding / Action row per account.
- **Account detail** — verdict banner, expected-vs-actual variance bar, a
  step-by-step derivation of the expected amount from contract clauses,
  claim lines + remittance, validation checklist, confidence, and recommended action.
- **Payer contract** — the sample Meridian Health Plan ↔ Riverside Regional agreement
  (case rates, per diem, DRG, % of charges, outlier/stop-loss, implant carve-out).
- **Validation logic** — the decision sequence plus the fields required from the
  contract and from the claim/remit.

## Sample accounts cover the full spectrum

| Account | Scenario | Finding |
|---------|----------|---------|
| A-100248 | Case rate not applied (paid % of charges) | Underpaid $1,610 |
| A-100402 | Outlier / stop-loss omitted | Underpaid $31,350 |
| A-100447 | Implant carve-out missing | Underpaid $14,160 |
| A-100311 | Per diem paid correctly | Correctly paid |
| A-100355 | Low paid-to-charge ratio, but gap is patient deductible | Correctly paid (false positive filtered) |
| A-100489 | Timely-filing denial | Routed to Denials |
