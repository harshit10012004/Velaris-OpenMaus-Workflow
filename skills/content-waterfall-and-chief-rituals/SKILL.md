---
name: content-waterfall-and-chief-rituals
description: Read-only knowledge graph content waterfall, engagement triage, and weekly Chief Room rituals.
---

# Content Waterfall & Chief Rituals Playbook

1. **Read-Only Knowledge Graph (`brief` & `progress`)**: Query `knowledge_graph` strictly with `read_only: true` (`max_results: 5` for briefs). Never write to the knowledge graph from sales or marketing flows.
2. **10-Piece Waterfall (`atomiser` -> `publisher`)**: Present `content_brief.json` for founder angle selection, generate 10 platform assets via `templates/atomiser_output.md.j2`, and publish cleared drafts via Buffer, X API, and Instagram API.
3. **Engagement Triage (`engagement`)**: Classify inbound comments/DMs into `pricing`, `general`, `feature_request`, or `spam`. Forward `pricing` to founder; auto-reply to `general` with `engagement_reply.md`.
4. **Chief Rituals (`digest`, `approval_gate`, `capacity_monitor`)**: Enforce daily capacity thresholds (`8` soft flag, `11` hard intake block), deliver Sunday `09:00` cross-room digest, and present 3 strategic decisions at Sunday `09:15`.
