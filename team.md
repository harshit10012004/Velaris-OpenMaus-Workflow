botmrr: 2
id: velaris-sales-workflow
release: "1.0.0"
name: Velaris Sales & Operations Team
tagline: Multi-room sim-racing telemetry lead pipeline, consent-gated delivery, and cross-border invoicing workflow.
summary: Coordinates five rooms across 21 specialized bots with founder approval gates, read-only knowledge graph queries, rule-based consent checks, and dead-letter logging.
outcomes:
  - Qualified sim-racing telemetry leads scored and synced across Notion and Supabase.
  - Founder-approved X outreach DMs with automated 7, 14, and 21-day follow-up cadences.
  - Guardian-consent-verified telemetry intake and two-gate MVO delivery packets.
  - Purpose-coded cross-border Stripe invoices, minor contract packets, and overdue collections.
  - Weekly Chief Room digests, daily capacity alerts, and a 10-piece content waterfall.
category: operations
author:
  name: Velaris-OC
  github: harshit10012004
  url: https://github.com/harshit10012004/Velaris-OpenMaus-Workflow
license: Apache-2.0
setupMinutes: 30
requirements:
  apps:
    - slug: discord
      label: Discord
      reason: Connect Discord for sim-racing lead acquisition.
    - slug: x-api
      label: X API
      reason: Search for relevant sim-racing posts and send founder-approved outreach.
    - slug: stripe
      label: Stripe
      reason: Create purpose-coded invoices and monitor overdue payments.
    - slug: notion
      label: Notion
      reason: Store and update the lead CRM.
    - slug: supabase
      label: Supabase
      reason: Store structured lead and workflow records.
    - slug: buffer
      label: Buffer
      reason: Distribute approved marketing content and collect performance metrics.
      optional: true
    - slug: instagram-api
      label: Instagram API
      reason: Publish approved Instagram content.
      optional: true
    - slug: drive
      label: Google Drive
      reason: Store telemetry uploads, delivery packets, invoices, and contracts.
    - slug: gmail
      label: Gmail
      reason: Send approved outreach, delivery, invoice, and contract messages.
    - slug: calendar
      label: Google Calendar
      reason: Propose and book founder-approved debrief slots.
    - slug: knowledge-graph
      label: LightRAG Knowledge Graph
      reason: Run read-only queries for progress notes and content briefs.
  capabilities: []
chiefOfStaff: digest
agents:
  - key: prospecting
    name: Prospecting
    title: Lead Acquisition Specialist
    description: Monitors sim-racing Discord channels and X posts for potential telemetry leads.
    skills:
      - sales-qualification-and-outreach
  - key: qualifier
    name: Qualifier
    title: Lead Qualification Specialist
    description: Scores leads from 0 to 100 and maps client type, jurisdiction, urgency, and recommended action.
    skills:
      - sales-qualification-and-outreach
  - key: outreach
    name: Outreach
    title: Founder-Gated Outreach Specialist
    description: Drafts personalized DMs from templates and routes them to the founder approval queue.
    skills:
      - sales-qualification-and-outreach
  - key: followup
    name: Follow-up
    title: Follow-up Coordinator
    description: Schedules 7, 14, and 21-day follow-ups for leads that have not replied.
    skills:
      - sales-qualification-and-outreach
  - key: crm
    name: CRM
    title: CRM Synchronization Specialist
    description: Synchronizes lead ID, client type, jurisdiction, stage, and last touch with Notion and Supabase.
  - key: digest
    name: Digest
    title: Chief of Staff Digest Lead
    description: Produces the weekly digest and broadcasts decisions and summaries across all rooms.
    skills:
      - content-waterfall-and-chief-rituals
  - key: approval_gate
    name: Approval Gate
    title: Strategic Decision Coordinator
    description: Presents strategic options across resources, product, channel, pricing, and capacity for founder approval.
  - key: capacity_monitor
    name: Capacity Monitor
    title: Delivery Capacity Monitor
    description: Monitors delivery load and enforces the soft threshold of 8 and hard intake-block threshold of 11.
  - key: intake
    name: Intake
    title: Telemetry Intake Validator
    description: Validates uploaded telemetry files and blocks intake until guardian consent is complete.
    skills:
      - guardian-consent-and-mvo-gating
  - key: delivery
    name: Delivery
    title: MVO Delivery Coordinator
    description: Executes MVO and family-summary delivery only after prescription and founder signoff gates are complete.
    skills:
      - guardian-consent-and-mvo-gating
  - key: progress
    name: Progress
    title: Client Progress Note Specialist
    description: Queries the knowledge graph in read-only mode and drafts weekly per-client progress notes.
  - key: scheduling
    name: Scheduling
    title: Debrief Scheduling Coordinator
    description: Proposes three founder calendar slots after debrief completion and books only after confirmation.
  - key: invoice
    name: Invoice
    title: Invoice Generation Specialist
    description: Generates micro-forensics invoices with lead ID and purpose-code metadata and saves PDF copies.
    skills:
      - cross-border-invoicing-and-collections
  - key: collections
    name: Collections
    title: Collections Follow-up Coordinator
    description: Coordinates 7, 14, and 21-day follow-ups for overdue invoices.
    skills:
      - cross-border-invoicing-and-collections
  - key: contract
    name: Contract
    title: Contract Packet Specialist
    description: Generates SOW, DPA, consent, and assent packets for minor client types C and D.
    skills:
      - cross-border-invoicing-and-collections
  - key: consent
    name: Consent
    title: Consent Validation Specialist
    description: Performs deterministic consent checks and blocks intake until the consent status is complete.
    skills:
      - guardian-consent-and-mvo-gating
  - key: brief
    name: Brief
    title: Content Brief Specialist
    description: Runs read-only knowledge graph queries with a maximum of five results to produce content briefs.
    skills:
      - content-waterfall-and-chief-rituals
  - key: atomiser
    name: Atomiser
    title: Content Repurposing Specialist
    description: Transforms approved content briefs into ten multi-platform pieces.
    skills:
      - content-waterfall-and-chief-rituals
  - key: publisher
    name: Publisher
    title: Content Distribution Specialist
    description: Publishes approved content across X, LinkedIn, and Instagram through approved integrations.
    skills:
      - content-waterfall-and-chief-rituals
  - key: engagement
    name: Engagement
    title: Community Engagement Triage Specialist
    description: Classifies comments and DMs into pricing, general, feature request, or spam categories.
    skills:
      - content-waterfall-and-chief-rituals
  - key: analytics
    name: Analytics
    title: Marketing Analytics Specialist
    description: Reports impressions, engagements, clicks, and growth into the Chief digest.
    skills:
      - content-waterfall-and-chief-rituals
rooms:
  - key: sales
    name: Sales Room
    bulletin: Lead acquisition, qualification, outreach, follow-up, and CRM synchronization.
    members:
      - prospecting
      - qualifier
      - outreach
      - followup
      - crm
    defaultResponder:
      kind: agent
      agent: prospecting
  - key: chief
    name: Chief Room
    bulletin: Founder coordination, weekly rituals, strategic decisions, and capacity monitoring.
    members:
      - digest
      - approval_gate
      - capacity_monitor
    defaultResponder:
      kind: agent
      agent: digest
  - key: delivery
    name: Delivery Room
    bulletin: Client onboarding, consent-gated intake, MVO delivery, progress notes, and debrief scheduling.
    members:
      - intake
      - delivery
      - progress
      - scheduling
    defaultResponder:
      kind: agent
      agent: intake
  - key: finance
    name: Finance Room
    bulletin: Invoicing, collections, consent, compliance, and cross-border operations.
    members:
      - invoice
      - collections
      - contract
      - consent
    defaultResponder:
      kind: agent
      agent: invoice
  - key: marketing
    name: Marketing Room
    bulletin: Content briefs, content waterfall, distribution, engagement, and analytics.
    members:
      - brief
      - atomiser
      - publisher
      - engagement
      - analytics
    defaultResponder:
      kind: agent
      agent: brief
routines:
  - key: sales_prospecting
    name: Sales Prospecting
    agent: prospecting
    prompt: Collect candidate sim-racing telemetry leads from approved Discord channels and X searches. Do not contact anyone automatically.
    runOn: maus
    durationMinutes: 30
    schedule:
      type: daily
      time: "09:00"
      weekdays:
        - mon
        - wed
        - fri
    enabledAfterInstall: false
  - key: sales_outreach_queue
    name: Sales Outreach Queue
    agent: outreach
    prompt: Draft and queue personalized outreach for founder review. Never send a message without explicit founder approval.
    runOn: maus
    durationMinutes: 30
    schedule:
      type: daily
      time: "10:00"
      weekdays:
        - tue
        - thu
        - sat
    enabledAfterInstall: false
  - key: chief_weekly_digest
    name: Chief Weekly Digest
    agent: digest
    prompt: Prepare the weekly digest across all rooms and present unresolved decisions to the founder.
    runOn: maus
    durationMinutes: 45
    schedule:
      type: daily
      time: "09:00"
      weekdays:
        - sun
    enabledAfterInstall: false
  - key: chief_daily_capacity
    name: Chief Daily Capacity Check
    agent: capacity_monitor
    prompt: Check delivery capacity and report threshold warnings. Do not block intake without the configured rule and user-visible notice.
    runOn: maus
    durationMinutes: 20
    schedule:
      type: daily
      time: "09:15"
      weekdays:
        - mon
        - tue
        - wed
        - thu
        - fri
        - sat
        - sun
    enabledAfterInstall: false
  - key: delivery_progress
    name: Delivery Progress Review
    agent: progress
    prompt: Draft weekly client progress notes using read-only knowledge graph queries and route recommendations for founder approval.
    runOn: maus
    durationMinutes: 30
    schedule:
      type: daily
      time: "09:00"
      weekdays:
        - mon
    enabledAfterInstall: false
  - key: marketing_analytics
    name: Marketing Analytics Review
    agent: analytics
    prompt: Prepare the weekly marketing performance report and send it to the Chief digest for review.
    runOn: maus
    durationMinutes: 30
    schedule:
      type: daily
      time: "10:00"
      weekdays:
        - sun
    enabledAfterInstall: false