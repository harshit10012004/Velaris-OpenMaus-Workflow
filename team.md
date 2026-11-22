---
botmrr: 2
id: velaris-sales-workflow
release: 1.0.0
name: Velaris Sales & Operations Team
tagline: A consent-gated sim-racing telemetry lead, delivery, finance, and content workflow.
summary: Coordinates five operational rooms and 21 specialized agents across lead discovery, qualification, founder-approved
  outreach, guardian-consent-gated telemetry intake, MVO delivery, cross-border invoicing, and approved content
  publishing.
category: operations
author:
  name: Velaris-OC
  url: https://github.com/harshit10012004/Velaris-OpenMaus-Workflow
license: Apache-2.0
setupMinutes: 30
outcomes:
- Qualified sim-racing telemetry leads scored and recorded in Notion and Supabase.
- Founder-reviewed outreach drafts and controlled 7/14/21-day follow-up workflows.
- Telemetry intake blocked until guardian consent is verified as complete.
- MVO and family-summary delivery gated by prescription and founder sign-off.
- Purpose-coded invoices, contract packets, and overdue-payment reminders.
- Weekly leadership reporting, capacity monitoring, and a ten-asset content workflow.
requirements:
  apps:
  - slug: discord
    label: Discord
    reason: Monitor sim-racing community discussions for relevant, public lead signals.
    optional: false
  - slug: x-api
    label: X (Twitter) API
    reason: Search public posts and support approved outreach workflows.
    optional: false
  - slug: stripe
    label: Stripe
    reason: Prepare and manage invoices and payment follow-up.
    optional: false
  - slug: notion
    label: Notion
    reason: Maintain the lead CRM and operational records.
    optional: false
  - slug: supabase
    label: Supabase
    reason: Store structured lead and workflow data.
    optional: false
  - slug: buffer
    label: Buffer
    reason: Schedule approved marketing content.
    optional: true
  - slug: instagram-api
    label: Instagram API
    reason: Support approved Instagram publishing and engagement workflows.
    optional: true
  - slug: drive
    label: Google Drive
    reason: Store telemetry uploads, delivery packets, invoices, and contracts.
    optional: false
  - slug: gmail
    label: Gmail
    reason: Send approved client communications and delivery emails.
    optional: false
  - slug: calendar
    label: Google Calendar
    reason: Find and book debrief slots after explicit confirmation.
    optional: false
  - slug: knowledge-graph
    label: LightRAG Knowledge Graph (Read-Only)
    reason: Retrieve relevant knowledge for progress notes and content briefs without writing to the graph.
    optional: false
  capabilities:
  - scheduled-routines
  - multi-agent-coordination
  - file-management
team:
  name: Velaris Operations
  leader: digest
  brief: 'Operate a five-room sim-racing telemetry service workflow. Preserve consent, privacy, founder approval,
    and delivery gates. Treat connector names as requirements only: each user must connect and authorize their own
    accounts. Never claim an action succeeded unless the relevant connector confirms it.'
agents:
- key: prospecting
  name: Prospecting Agent
  description: 'Lead acquisition; monitors sim-racing Discord channels and X posts. Suggested model: openrouter/free.'
  appearance:
    color: blue
  approval: auto
  title: Sales specialist
- key: qualifier
  name: Lead Qualifier
  description: 'Scores leads 0–100 and classifies client type A–D, jurisdiction IN/AE/MY/SG, urgency, and recommended
    action. Suggested model: opencode/nemotron-3-super-free.'
  appearance:
    color: cyan
  approval: auto
  title: Sales specialist
- key: outreach
  name: Outreach Drafter
  description: 'Drafts personalized messages from approved templates and queues them for founder approval. Suggested
    model: openrouter/gemma-4-26b-a4b-it:free.'
  appearance:
    color: green
  approval: ask
  title: Sales specialist
- key: followup
  name: Follow-up Scheduler
  description: 'Coordinates 7/14/21-day follow-ups only when a lead has not replied. Suggested model: mimo-v2.5-free.'
  appearance:
    color: purple
  approval: auto
  title: Sales specialist
- key: crm
  name: CRM Synchronizer
  description: Maintains lead_id, client_type, jurisdiction, stage, and last_touch in Notion and Supabase.
  appearance:
    color: orange
  approval: auto
  title: Sales specialist
- key: digest
  name: Chief of Staff Digest
  description: 'Compiles weekly summaries across all rooms and reports to the founder. Suggested model: openrouter/minimax-m3.1-flash:free.'
  appearance:
    color: blue
  approval: auto
  title: Chief specialist
- key: approval_gate
  name: Founder Approval Gate
  description: Presents strategic choices covering resources, product, channels, pricing, and capacity; never approves
    its own proposals.
  appearance:
    color: cyan
  approval: ask
  title: Chief specialist
- key: capacity_monitor
  name: Capacity Monitor
  description: Checks delivery queue capacity; soft threshold 8 and hard intake-block threshold 11.
  appearance:
    color: green
  approval: auto
  title: Chief specialist
- key: intake
  name: Telemetry Intake Validator
  description: Validates uploaded telemetry files and blocks intake until guardian consent is complete.
  appearance:
    color: purple
  approval: auto
  title: Delivery specialist
- key: delivery
  name: MVO Delivery Coordinator
  description: Coordinates MVO and family-summary delivery only after prescription and founder sign-off gates.
  appearance:
    color: orange
  approval: ask
  title: Delivery specialist
- key: progress
  name: Client Progress Drafter
  description: 'Drafts weekly client progress notes using read-only knowledge-graph queries; founder approval required
    for recommendations. Suggested model: opencode/nemotron-3-super-free.'
  appearance:
    color: blue
  approval: ask
  title: Delivery specialist
- key: scheduling
  name: Debrief Scheduler
  description: 'Proposes three founder-calendar slots after debrief completion and books only after confirmation.
    Suggested model: mimo-v2.5-free.'
  appearance:
    color: cyan
  approval: ask
  title: Delivery specialist
- key: invoice
  name: Invoice Generator
  description: 'Prepares purpose-coded Stripe invoices with lead_id metadata and saves PDF copies; requires founder
    approval before sending. Suggested model: openrouter/north-mini-code:free.'
  appearance:
    color: green
  approval: ask
  title: Finance specialist
- key: collections
  name: Collections Coordinator
  description: 'Manages overdue invoice reminders on a 7/14/21-day cadence. Suggested model: mimo-v2.5-free.'
  appearance:
    color: purple
  approval: auto
  title: Finance specialist
- key: contract
  name: Contract Packet Generator
  description: Prepares SOW, DPA, consent pack, and assent forms for client types C and D; founder approval required
    before dispatch.
  appearance:
    color: orange
  approval: ask
  title: Finance specialist
- key: consent
  name: Consent Validator
  description: Applies deterministic consent checks and blocks intake until consent status is complete; do not infer
    consent.
  appearance:
    color: blue
  approval: auto
  title: Finance specialist
- key: brief
  name: Content Brief Researcher
  description: 'Uses read-only knowledge-graph queries, capped at five results, to prepare content briefs for founder
    angle selection. Suggested model: openrouter/free.'
  appearance:
    color: cyan
  approval: ask
  title: Marketing specialist
- key: atomiser
  name: Content Atomiser
  description: 'Turns approved briefs into ten platform-specific draft assets for review. Suggested model: openrouter/gemma-4-26b-a4b-it:free.'
  appearance:
    color: green
  approval: ask
  title: Marketing specialist
- key: publisher
  name: Content Publisher
  description: Publishes only founder-approved content to X, LinkedIn, and Instagram using configured connectors.
  appearance:
    color: purple
  approval: ask
  title: Marketing specialist
- key: engagement
  name: Engagement Triage
  description: 'Classifies inbound comments and DMs as pricing, general, feature_request, or spam; routes pricing
    to founder. Suggested model: liquid/lfm-2.5-2.6b:free.'
  appearance:
    color: orange
  approval: ask
  title: Marketing specialist
- key: analytics
  name: Marketing Analytics Reporter
  description: Reports impressions, engagements, clicks, and growth into the Chief digest.
  appearance:
    color: blue
  approval: auto
  title: Marketing specialist
rooms:
- key: sales
  name: Sales Room
  members:
  - prospecting
  - qualifier
  - outreach
  - followup
  - crm
  defaultResponder:
    kind: agent
    agent: prospecting
  bulletin: Discover and qualify relevant leads. Outreach must be drafted for founder approval before sending.
- key: chief
  name: Chief Room
  members:
  - digest
  - approval_gate
  - capacity_monitor
  defaultResponder:
    kind: agent
    agent: digest
  bulletin: Coordinate leadership reporting, strategic approvals, and delivery capacity. Escalate decisions to the
    founder.
- key: delivery
  name: Delivery Room
  members:
  - intake
  - delivery
  - progress
  - scheduling
  defaultResponder:
    kind: agent
    agent: intake
  bulletin: Do not accept or deliver client telemetry work until consent and both MVO approval gates are satisfied.
- key: finance
  name: Finance Room
  members:
  - invoice
  - collections
  - contract
  - consent
  defaultResponder:
    kind: agent
    agent: invoice
  bulletin: Prepare invoices and contract documents carefully. Founder approval is required before external dispatch
    where specified.
- key: marketing
  name: Marketing Room
  members:
  - brief
  - atomiser
  - publisher
  - engagement
  - analytics
  defaultResponder:
    kind: agent
    agent: brief
  bulletin: Research and draft content; publish only material that has received founder approval.
routines:
- key: sales_prospecting_and_qualification
  name: Sales prospecting and qualification
  agent: prospecting
  prompt: Review the configured Discord and X public-source queues, identify relevant sim-racing telemetry prospects,
    and pass candidates to the qualifier. Record only necessary business-relevant data. Do not send messages.
  runOn: cloud
  schedule:
    type: cron
    expression: 0 9 * * 1,3,5
    timeZone: Asia/Kolkata
  durationMinutes: 25
  enabledAfterInstall: false
  overlap: skip
- key: sales_outreach_queue
  name: Sales outreach review queue
  agent: outreach
  prompt: Prepare personalized outreach drafts for qualified leads using the approved outreach template. Place drafts
    in the founder approval queue. Do not send unless explicit approval is recorded; after an approved send, let
    the follow-up agent manage the 7/14/21-day cadence.
  runOn: cloud
  schedule:
    type: cron
    expression: 0 9 * * 2,4,6
    timeZone: Asia/Kolkata
  durationMinutes: 25
  enabledAfterInstall: false
  overlap: skip
- key: chief_weekly_digest_and_decisions
  name: Weekly Chief digest and decisions
  agent: digest
  prompt: Compile the weekly digest from all rooms, then prepare strategic decision options for the founder covering
    resources, product, channels, pricing, and capacity. The approval gate must present options, not make the founder's
    decision.
  runOn: cloud
  schedule:
    type: cron
    expression: 0 9 * * 0
    timeZone: Asia/Kolkata
  durationMinutes: 30
  enabledAfterInstall: false
  overlap: skip
- key: chief_daily_capacity_check
  name: Daily delivery capacity check
  agent: capacity_monitor
  prompt: Check the Delivery Room queue. At 8 active items, flag capacity in the Chief digest. At 11, recommend
    or apply the configured intake block and notify the founder. Do not delete or silently discard queued work.
  runOn: cloud
  schedule:
    type: cron
    expression: 0 9 * * *
    timeZone: Asia/Kolkata
  durationMinutes: 15
  enabledAfterInstall: false
  overlap: skip
- key: delivery_intake_and_weekly_progress
  name: Delivery intake and weekly progress
  agent: intake
  prompt: Review pending telemetry intake items during the configured Mon–Sat operating window. Validate file presence
    and consent status; block intake unless guardian consent is explicitly complete. On Mondays, ask the progress
    agent to prepare weekly client notes using read-only knowledge-graph access. Do not deliver MVO materials without
    both Gate 1 prescription and Gate 2 founder sign-off.
  runOn: cloud
  schedule:
    type: cron
    expression: 0 9 * * 1-6
    timeZone: Asia/Kolkata
  durationMinutes: 30
  enabledAfterInstall: false
  overlap: skip
- key: marketing_brief_engagement_and_analytics
  name: Marketing workflow review
  agent: brief
  prompt: Review content-brief requests and prepare briefs from at most five read-only knowledge-graph results.
    Coordinate daily engagement triage and weekly metrics reporting through the assigned agents. Content atomisation
    and publishing remain approval-gated; never publish unapproved content.
  runOn: cloud
  schedule:
    type: cron
    expression: 0 10 * * 0,1,4
    timeZone: Asia/Kolkata
  durationMinutes: 30
  enabledAfterInstall: false
  overlap: skip
---

# Velaris Sales & Operations Team

A five-room workflow for sim-racing telemetry services, with explicit consent, founder-approval, and delivery safeguards.

## Activation

Import this repository folder using OpenMausBot Desktop's **Import…** action. Connect only the integrations your workspace actually uses, review each permission, and verify the configured account and data scope before enabling any workflow. All six routines arrive paused.

## Mission

Coordinate lead acquisition, qualification, approved outreach, consent-verified telemetry intake, MVO delivery, invoicing, contract preparation, and marketing operations without bypassing human approval or consent requirements.

## Outcomes

- Qualified leads with documented score, client type, jurisdiction, urgency, and next action.
- Outreach drafts held for founder approval, with follow-up only after an approved send and no reply.
- Telemetry intake blocked until guardian consent is explicitly verified as complete.
- MVO and family-summary delivery only after prescription (Gate 1) and founder sign-off (Gate 2).
- Purpose-coded Stripe invoices, client contract packets, and controlled collections reminders.
- Weekly Chief reporting, capacity alerts, and founder-reviewed multi-platform content.

## Connections

- **Discord:** monitor configured sim-racing community channels.
- **X (Twitter) API:** discover public posts and support approved outreach.
- **Stripe:** prepare invoices and monitor payment status.
- **Notion / Supabase:** maintain CRM records and structured workflow data.
- **Google Drive:** store uploads, delivery packets, invoices, and contracts.
- **Gmail:** send communications only after the required approval.
- **Google Calendar:** propose debrief slots and book only after confirmation.
- **Buffer / Instagram API:** optional distribution tools for approved content.
- **LightRAG Knowledge Graph:** read-only retrieval; never write or modify graph data.

A listed connector is not authorization. Each operator must connect their own account and grant only the required permissions. If a connector is unavailable, report the limitation rather than pretending the action completed.

## Team

### Sales Room
- **Prospecting:** monitors configured Discord channels (including iRacing Help, ACC Questions, and LUM Support) and public X search terms such as “iRating”, “lap time”, and “data analysis”.
- **Qualifier:** records `lead_id`, `client_type` (A–D), `jurisdiction` (IN, AE, MY, SG), score (0–100), urgency, and recommended action.
- **Outreach:** drafts personalized messages from `templates/outreach_dm.md.j2`; queues them for founder approval. A rejection routes the lead to nurture.
- **Follow-up:** manages the 7/14/21-day no-reply cadence only after a permitted initial outreach.
- **CRM:** synchronizes `lead_id`, `client_type`, `jurisdiction`, `stage`, and `last_touch` with Notion and Supabase.

### Chief Room
- **Digest:** compiles weekly reports across all rooms.
- **Approval gate:** presents strategic options for founder decision; it cannot approve its own proposals.
- **Capacity monitor:** flags the soft threshold of 8 active delivery items and the hard threshold of 11.

### Delivery Room
- **Intake:** validates files in Drive's `telemetry_uploads` area and blocks intake unless guardian consent is explicitly `complete`.
- **Delivery:** sends `mvo.md` and `family_summary.md` only after `mvo_gate_1` (prescription authored) and `mvo_gate_2` (founder sign-off); archives approved outputs under `client_deliveries/{lead_id}/{date}`.
- **Progress:** drafts weekly client notes using read-only knowledge-graph queries (maximum five results); recommendations require founder approval.
- **Scheduling:** proposes three available founder-calendar slots after debrief completion and books only after confirmation.

### Finance Room
- **Invoice:** prepares Stripe `micro_forensics` invoices with `lead_id` and `purpose_code` metadata, saves PDF copies, and queues external dispatch for founder approval.
- **Collections:** coordinates overdue reminders on a 7/14/21-day cadence.
- **Contract:** prepares SOW, DPA, consent pack, and assent form packets for client types C and D; founder approval is required before sending.
- **Consent:** performs deterministic rule-based checks. It must not infer consent from silence, uploaded files, or an incomplete signature record.

### Marketing Room
- **Brief:** creates `content_brief.json` from no more than five read-only knowledge-graph results.
- **Atomiser:** turns an approved brief into ten platform-specific drafts using `templates/atomiser_output.md.j2`.
- **Publisher:** distributes only founder-approved content to X, LinkedIn, and Instagram.
- **Engagement:** classifies inbound comments and DMs as pricing, general, feature_request, or spam; pricing queries go to the founder.
- **Analytics:** reports impressions, engagements, clicks, and growth to the Chief digest.

## Chief of Staff

The Chief of Staff is **Digest** (`digest`). It coordinates weekly reporting and escalates strategic decisions, consent exceptions, capacity blocks, and approval requests to the founder. It does not override room-level safeguards.

## Completion rule

A task is complete only when its expected output is verified in the destination system and any required human approval is recorded. Never claim a message was sent, an invoice was issued, a booking was made, consent was obtained, or content was published without confirmation from the relevant system. Keep all routines paused until the founder explicitly enables them. Never store API keys, passwords, or private credentials in this template.
