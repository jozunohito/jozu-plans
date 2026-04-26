---
name: Jozu tooling & external systems
description: Where things live — GitHub, GoDaddy, Airtable, Cloudflare, Google Analytics, RGI BDR team, LinkedIn
type: reference
originSessionId: b76896f1-74c9-4dc1-9c8f-284044f2d492
---
**GitHub** — primary hosting. Org/user: `jozunohito`. Four public repos as of 2026-04-22:
- `jozu-plans`: https://github.com/jozunohito/jozu-plans — 55 GTM plan HTML pages. GitHub Pages not enabled.
- `jozu-website`: https://github.com/jozunohito/jozu-website — source of the live site at jozuconsultinggroup.com. CNAME file in repo configures custom domain via GitHub Pages. Cloudflare proxies DNS.
- `value-wedge-system`: https://github.com/jozunohito/value-wedge-system — standalone presentation of the complete Value Wedge / Deep Discovery / Power Messaging / Buying Cycle Gates / Mutual Sequence framework. Doctrinal source material.
- `80-20-revenue-plan`: https://github.com/jozunohito/80-20-revenue-plan — not yet ingested.

Push access: not currently configured in this session (wiped). Need to re-establish GitHub auth (PAT or SSH key) before any write-back to the live site or plans can happen.

**Remote Trigger routines (claude.ai/code)**
- `jozu-role-search`: ID `trig_01GE5guWsQT1HfKs3EX6fvRm`. 8-hour cron (06:00, 14:00, 22:00 UTC = 00:00, 08:00, 16:00 America/Denver). Hunts global CRO/Head of Sales/Founding Sales roles at funded companies with US-launch signals, Japan priority. Writes results to `role_search/results.jsonl` and `role_search/runs/` inside jozu-plans repo. Output viewable at https://claude.ai/code/routines/trig_01GE5guWsQT1HfKs3EX6fvRm.

**Local session persistence**
- Session logs: `C:\Users\Jeff\claude-projects\sessions\session_YYYY-MM-DD.md`
- Session state files (from prior sessions): `C:\Users\Jeff\claude-projects\sessions\session_state_YYYY-MM-DD.md`
- Brand assets: `C:\Users\Jeff\claude-projects\brand\`

**GoDaddy** — registrar for jozuconsultinggroup.com domain.

**Airtable** — **collaboration hub between Jeff and RGI, NOT a CRM.** Two distinct uses going forward:
1. **Jozu side (Kimi-operated):** Kimi runs Jozu's outreach work in Airtable from now on. Claude Code does not edit Jozu-side tables.
2. **Jeff role-search side (Claude-operated):** a dedicated table feeds RGI nightly with manually confirmed LinkedIn connection notes for CEOs / leaders at every firm Jeff has applied to. RGI runs Aimfox against this table every few hours to automate the connection-request outreach. Schema and workflow defined in `project_aimfox_rgi_outreach_queue.md`.

**Folk CRM** — Jeff's owned CRM. Helped him select and set it up. Not yet integrated into the live workflow. Reserve for when pipeline justifies migration off Airtable-as-tracker.

**Apollo** — Jeff owns it. Sales engagement / lead enrichment platform. Not yet integrated into the live workflow.

**Aimfox** — RGI's LinkedIn outreach automation tool. RGI runs Aimfox against the Airtable outreach queue Claude maintains. Aimfox sends connection requests with the manually confirmed note attached to each row.

**RGI** — external BDR team that executes LinkedIn and email outreach. They consume the Aimfox queue from Airtable.

**Cloudflare** — analytics (and likely DNS/CDN) for jozuconsultinggroup.com and hosted plan pages.

**Google Analytics** — analytics on jozuconsultinggroup.com and the various hosted plan pages sent to prospects.

**LinkedIn** — Jeff's profile: https://www.linkedin.com/in/jeffreyaragon (public view is auth-gated; full profile not scrapable without login).

**Website:** https://www.jozuconsultinggroup.com

**How to use:** When Jeff references "the plans," "the site," "the lists," or "outreach," default to these systems. Ask before assuming a new tool is needed — the answer is almost always "already exists in one of these."
