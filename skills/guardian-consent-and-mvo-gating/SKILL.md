---
name: guardian-consent-and-mvo-gating
description: Deterministic guardian consent verification and two-gate MVO delivery controls.
---

# Guardian Consent & MVO Gating Playbook

1. **Zero-LLM Consent Verification (`consent` & `intake`)**: Validate guardian consent packs using deterministic rules only (`rule_based: true`). Block telemetry intake until `consent_status == complete`.
2. **Two-Gate MVO Signoff (`delivery`)**:
   - `mvo_gate_1`: Founder authors the technical prescription (`auto_advance: false`).
   - `mvo_gate_2`: Founder signs off on `mvo.md` and `family_summary.md` (`auto_advance: false`).
3. **Delivery & Archival**: After `gate_2_signed`, send `mvo_delivery.md` with `mvo.md` and `family_summary.md` via Gmail and archive copies to `client_deliveries/{lead_id}/{date}` in Drive.
4. **Debrief Scheduling (`scheduling`)**: Upon `debrief_complete`, offer 3 available slots from `founder_calendar` and book on confirmation.
