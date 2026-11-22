---
name: sales-qualification-and-outreach
description: Lead capture, structured scoring, founder-gated DM outreach, and dual CRM synchronization.
---

# Sales Qualification & Outreach Playbook

1. **Prospecting Feed (`prospecting`)**: Collect candidate threads from Discord (`iRacing Help`, `ACC Questions`, `LUM Support`) and X (`stuck at`, `iRating`, `data analysis`, `lap time`). Keep `auto_advance: false`.
2. **Classification Schema (`qualifier`)**: Output strict JSON matching:
   - `lead_id`: string
   - `client_type`: `A` | `B` | `C` | `D`
   - `jurisdiction`: `IN` | `AE` | `MY` | `SG`
   - `score`: integer `0`..`100`
   - `urgency`: `high` | `medium` | `low`
   - `recommended_action`: `outreach` | `nurture` | `disqualify`
3. **Founder Outreach Gate (`outreach`)**: Render `templates/outreach_dm.md.j2` and hold for founder approval (`48h` timeout). On approve, dispatch X DM and trigger `followup` (`7/14/21 days`). On reject, move lead to `nurture`.
4. **CRM Sync (`crm`)**: Upsert `lead_id`, `client_type`, `jurisdiction`, `stage`, and `last_touch` in Notion (`leads`) and Supabase (`public.leads`).
