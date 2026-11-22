---
name: cross-border-invoicing-and-collections
description: Minor contract packets, purpose-coded Stripe invoicing, and overdue collections cadence.
---

# Cross-Border Invoicing & Collections Playbook

1. **Minor Client Contract Packet (`contract`)**: Trigger when `client_type` is `C` or `D`. Generate `sow.md`, `dpa.md`, `consent_pack.md`, and `assent_form.md` in `contracts/{client_type}/` and route `contract_submission.md` to founder gate (`48h` timeout).
2. **Purpose-Coded Invoicing (`invoice`)**: On `project_complete`, draft Stripe invoice for `micro_forensics` carrying `lead_id` and `purpose_code` metadata, save `invoices/{invoice_id}.pdf` to Drive, and hold at founder gate (`24h` timeout).
3. **Collections Cadence (`collections`)**: On Stripe `overdue` status, dispatch `collections_reminder.md` on a `7/14/21 days` cadence.
