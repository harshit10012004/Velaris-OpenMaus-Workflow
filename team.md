---
botmrr: 2
id: velaris-sales-workflow
release: "1.0.0"
name: Velaris Sales & Operations Team
tagline: Multi-room sim-racing telemetry lead pipeline, consent-gated delivery, and cross-border invoicing workflow.
summary: Coordinates five rooms (Sales, Chief, Delivery, Finance, Marketing) across 21 specialized bots with founder approval gates, read-only knowledge graph queries, rule-based consent checks, and dead-letter logging.
category: operations
author:
  name: Velaris-OC
  github: harshit10012004
  url: https://github.com/harshit10012004/Velaris-OpenMaus-Workflow
license: Apache-2.0
setupMinutes: 30
requirements:
  connectors:
    - discord
    - x_api
    - stripe
    - notion
    - supabase
    - buffer
    - instagram_api
    - drive
    - gmail
    - calendar
    - knowledge_graph
team:
  chief_of_staff: digest
  rooms:
    - slug: sales
      name: Sales Room
      description: Lead acquisition, qualification, and outreach
      color: "#e3f2fd"
    - slug: chief
      name: Chief Room
      description: Founder coordination, weekly rituals, capacity monitoring
      color: "#f3e5f5"
    - slug: delivery
      name: Delivery Room
      description: Client onboarding, MVO delivery, debrief scheduling
      color: "#f3e5f5"
    - slug: finance
      name: Finance Room
      description: Invoicing, compliance, cross-border operations
      color: "#e8f5e9"
    - slug: marketing
      name: Marketing Room
      description: Content waterfall, distribution, analytics
      color: "#e8fdae"
agents:
  - name: prospecting
    role: Lead acquisition agent monitoring sim-racing Discord channels and X posts
    room: sales
    model_hint: openrouter/free
    approval_required: false
  - name: qualifier
    role: Structured lead classifier scoring leads (0-100) and mapping client_type (A-D) and jurisdiction (IN, AE, MY, SG)
    room: sales
    model_hint: opencode/nemotron-3-super-free
    approval_required: false
  - name: outreach
    role: Drafts personalized DMs from templates/outreach_dm.md.j2 and routes to founder approval queue
    room: sales
    model_hint: openrouter/gemma-4-26b-a4b-it:free
    approval_required: true
  - name: followup
    role: Event-driven follow-up scheduler for no-reply leads on a 7/14/21 day cadence
    room: sales
    model_hint: mimo-v2.5-free
    approval_required: false
  - name: crm
    role: CRUD logger syncing lead_id, client_type, jurisdiction, stage, and last_touch to Notion and Supabase
    room: sales
    model_hint: null
    approval_required: false
  - name: digest
    role: Chief of Staff weekly summariser broadcasting weekly digest across all rooms
    room: chief
    model_hint: openrouter/minimax-m3.1-flash:free
    approval_required: false
  - name: approval_gate
    role: Weekly strategic decision maker presenting 3 options across resource, product, channel, pricing, and capacity
    room: chief
    model_hint: openrouter/free
    approval_required: true
  - name: capacity_monitor
    role: Daily delivery queue monitor enforcing soft threshold 8 and hard threshold 11 intake block
    room: chief
    model_hint: null
    approval_required: false
  - name: intake
    role: Validates uploaded telemetry files and blocks intake until guardian consent status is complete
    room: delivery
    model_hint: null
    approval_required: false
  - name: delivery
    role: Executes MVO and family summary delivery after Gate 1 prescription and Gate 2 signoff
    room: delivery
    model_hint: null
    approval_required: true
  - name: progress
    role: Weekly per-client progress note drafter querying knowledge graph in read-only mode
    room: delivery
    model_hint: opencode/nemotron-3-super-free
    approval_required: conditional
  - name: scheduling
    role: Proposes 3 founder calendar slots after debrief completion and schedules upon confirmation
    room: delivery
    model_hint: mimo-v2.5-free
    approval_required: true
  - name: invoice
    role: Generates micro_forensics invoices with lead_id and purpose_code metadata and saves PDFs
    room: finance
    model_hint: openrouter/north-mini-code:free
    approval_required: true
  - name: collections
    role: Overdue invoice follow-up scheduler running on a 7/14/21 day cadence
    room: finance
    model_hint: mimo-v2.5-free
    approval_required: false
  - name: contract
    role: Generates SOW, DPA, consent pack, and assent form packets for minor client types C and D
    room: finance
    model_hint: null
    approval_required: true
  - name: consent
    role: Rule-based consent validator blocking intake until consent status is complete without model calls
    room: finance
    model_hint: null
    approval_required: false
  - name: brief
    role: Queries knowledge graph in read-only mode (max 5 results) to produce content briefs
    room: marketing
    model_hint: openrouter/free
    approval_required: true
  - name: atomiser
    role: Transforms approved content briefs into 10 multi-platform pieces from templates/atomiser_output.md.j2
    room: marketing
    model_hint: openrouter/gemma-4-26b-a4b-it:free
    approval_required: true
  - name: publisher
    role: Publishes approved content across X, LinkedIn, and Instagram via Buffer and native APIs
    room: marketing
    model_hint: null
    approval_required: false
  - name: engagement
    role: Daily triage bot classifying comments and DMs into pricing, general, feature_request, or spam
    room: marketing
    model_hint: liquid/lfm-2.5-2.6b:free
    approval_required: conditional
  - name: analytics
    role: Weekly performance reporter feeding impressions, engagements, clicks, and growth into chief digest
    room: marketing
    model_hint: null
    approval_required: false
skills:
  - sales-qualification-and-outreach
  - guardian-consent-and-mvo-gating
  - cross-border-invoicing-and-collections
  - content-waterfall-and-chief-rituals
routines:
  - name: sales_prospecting_and_qualification
    schedule: "Mon, Wed, Fri"
    enabledAfterInstall: false
  - name: sales_outreach_queue
    schedule: "Tue, Thu, Sat"
    enabledAfterInstall: false
  - name: chief_weekly_digest_and_decisions
    schedule: "Sun 09:00 / Sun 09:15"
    enabledAfterInstall: false
  - name: chief_daily_capacity_check
    schedule: "Daily 09:00"
    enabledAfterInstall: false
  - name: delivery_intake_and_weekly_progress
    schedule: "Mon-Sat intake / Mon 09:00 progress"
    enabledAfterInstall: false
  - name: marketing_brief_engagement_and_analytics
    schedule: "Mon, Thu brief / Daily 09:00 engagement / Sun 10:00 analytics"
    enabledAfterInstall: false
---

# Velaris Sales & Operations Team

Multi-room telemetry operations workflow covering lead acquisition, structured qualification, guardian-consent-gated MVO delivery, cross-border Stripe invoicing, and a 10-piece content waterfall.

## Setup Checklist
1. Import this template folder into OpenMausBot Desktop via **Import…**.
2. Connect required integrations in **Apps / Connectors** (`discord`, `x_api`, `stripe`, `notion`, `supabase`, `buffer`, `instagram_api`, `drive`, `gmail`, `calendar`, and read-only `knowledge_graph`).
3. Configure dead-letter logging (`{timestamp}_{script}_{bot}.json`, 365-day retention) in your workspace settings and enable routines after reviewing founder gates.

## Room Architecture

### Sales Room (`sales`)
- **prospecting** (`openrouter/free`, Mon/Wed/Fri): Monitors Discord channels (`iRacing Help`, `ACC Questions`, `LUM Support`) and X search keywords (`stuck at`, `iRating`, `data analysis`, `lap time`). Uses manual feed queue (`auto_advance: false`).
- **qualifier** (`opencode/nemotron-3-super-free`, Mon/Wed/Fri): Classifies leads into `lead_id`, `client_type` (`A`, `B`, `C`, `D`), `jurisdiction` (`IN`, `AE`, `MY`, `SG`), `score` (`0`–`100`), `urgency` (`high`, `medium`, `low`), and `recommended_action` (`outreach`, `nurture`, `disqualify`).
- **outreach** (`openrouter/gemma-4-26b-a4b-it:free`, Tue/Thu/Sat): Drafts DMs using `templates/outreach_dm.md.j2` and holds in founder approval queue (`48h` timeout; `on_reject: nurture`, `on_approve: send_dm_and_start_followup`).
- **followup** (`mimo-v2.5-free`, event-driven): Sends automated follow-ups on a `7/14/21 days` cadence when there is no reply.
- **crm** (deterministic CRUD, event-driven): Upserts `lead_id`, `client_type`, `jurisdiction`, `stage`, and `last_touch` into Notion (`leads`) and Supabase (`public.leads`).

### Chief Room (`chief`)
- **digest** (`openrouter/minimax-m3.1-flash:free`, Sun `09:00`): Aggregates summaries across all rooms and broadcasts the weekly digest to the founder.
- **approval_gate** (`openrouter/free`, Sun `09:15`): Presents 3 strategic decisions across `resource_allocation`, `product_change`, `channel_shift`, `pricing_change`, and `capacity_adjustment` (`24h` timeout fallback).
- **capacity_monitor** (deterministic monitor, Daily `09:00`): Checks Delivery Room file count with soft threshold `8` (`digest_flag`) and hard threshold `11` (`block_intake`).

### Delivery Room (`delivery`)
- **intake** (deterministic validator, Mon–Sat): Validates files in Drive `telemetry_uploads` and blocks intake unless guardian consent status is `complete`.
- **delivery** (deterministic sender, event `gate_2_signed`): Enforces `mvo_gate_1` (prescription authored) and `mvo_gate_2` (founder signoff) before sending `mvo.md` and `family_summary.md` via Gmail and archiving to `client_deliveries/{lead_id}/{date}` in Drive.
- **progress** (`opencode/nemotron-3-super-free`, Mon `09:00`): Queries the knowledge graph in read-only mode to draft weekly per-client progress notes; requires founder approval if recommendations are included.
- **scheduling** (`mimo-v2.5-free`, event `debrief_complete`): Finds 3 open slots on `founder_calendar` and confirms debrief booking.

### Finance Room (`finance`)
- **invoice** (`openrouter/north-mini-code:free`, event `project_complete`): Creates Stripe `micro_forensics` invoices with `lead_id` and `purpose_code` metadata, saves `invoices/{invoice_id}.pdf` to Drive, emails `invoice_template.md`, and routes to founder gate (`24h` timeout).
- **collections** (`mimo-v2.5-free`, event `overdue`): Sends `collections_reminder.md` on a `7/14/21 days` cadence for overdue Stripe invoices.
- **contract** (deterministic generator, event `client_type_cd`): Generates `sow.md`, `dpa.md`, `consent_pack.md`, and `assent_form.md` for minor client types `C` and `D` into `contracts/{client_type}/` and emails `contract_submission.md` after founder approval (`48h` timeout).
- **consent** (deterministic validator, event `signature_received`): Runs rule-based consent verification (`rule_based: true`, zero LLM calls) and unlocks intake only when `consent_status == complete`.

### Marketing Room (`marketing`)
- **brief** (`openrouter/free`, Mon/Thu): Queries the knowledge graph (`read_only: true`, `max_results: 5`) to emit `content_brief.json` for founder angle selection.
- **atomiser** (`openrouter/gemma-4-26b-a4b-it:free`, event `brief_approved`): Expands an approved brief into 10 platform drafts via `templates/atomiser_output.md.j2` for founder review.
- **publisher** (deterministic publisher, event `approval_cleared`): Publishes approved content to X, LinkedIn, and Instagram via Buffer and native APIs.
- **engagement** (`liquid/lfm-2.5-2.6b:free`, Daily `09:00`): Classifies comments and DMs (`pricing`, `general`, `feature_request`, `spam`), routing pricing queries to the founder and auto-replying to general queries with `engagement_reply.md`.
- **analytics** (deterministic reporter, Sun `10:00`): Pulls Buffer and X metrics (`impressions`, `engagements`, `clicks`, `growth`) into the Chief digest.