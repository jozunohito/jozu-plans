---
name: Jozu agent operating system inventory
description: Current live Claude Code Routines agents feeding Jeff's Jozu operation. Trigger IDs and cadences as of 2026-04-24.
type: reference
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## Live agents (all at claude.ai/code/routines)

| Agent | Trigger ID | Cadence | Output |
|-------|------------|---------|--------|
| jozu-role-search | trig_01GE5guWsQT1HfKs3EX6fvRm | Every 12h :00 UTC | Tier 1 roles → /tier1/inbox/ (repo); Tier 2 prospects → Airtable |
| jozu-rfp-fed-intel | trig_015Mg46ZXo7oghqQbEtxsFCf | Every 12h :17 UTC | /intel/jozu-rfp-fed-intel/ (USAJOBS, JETRO, accelerators) |
| jozu-apac-sourcing | trig_01Fvn8a8w5JffnMhnoUpncwB | Every 12h :25 UTC | Native-language Japan/Korea/China/SEA/ANZ sources |
| jozu-emea-sourcing | trig_01TwWF5bzyWBigiDuaMCwsTd | Every 12h :30 UTC | Native-language UK/EU/Israel/MEA sources |
| jozu-qa-watchdog | trig_01EmQ7mo4Tv8QHh8LS6zZ4WX | Every 12h :40 UTC | /qa/LATEST.md + GitHub issue on FAIL |
| jozu-signals | trig_01NaZYCUzyFrnMHymBbRigCT | Every 12h :50 UTC | Trigger-event enrichment on Airtable rows |
| jozu-application-drafter | trig_014wb6St57DCEAhs4uRP1kZe | Daily 11:00 UTC / 5 AM MDT | /applications/<slug>/ cover letters + bullets |
| jozu-warm-network | trig_01AF1whGdx9sEjX5xLgzoQRT | Daily 13:00 UTC / 7 AM MDT | Cross-refs /config/network_jeff.csv vs Airtable |
| jozu-networking-events | trig_01XjofRoeAzFFkqkoRLHQSVf | Daily 14:00 UTC / 8 AM MDT | /events/YYYY-MM-DD.md (Pavilion, SaaStr, JETRO, Denver, etc.) |

**Daily run math:** 6 twice-daily + 3 daily = 15 runs/day. Exactly at the Max 20x included-runs ceiling.

## Disabled (do not re-enable)

- trig_01PB8goTx88tkFaV2qBvpofh — duplicate jozu-rfp-fed-intel accidentally created 2026-04-24 before dedup check. Disabled same night.
- trig_01FNYuTMeEF9HBALwbQEBAV5 — legacy Precision Role Finder (pre-wipe). Auto-disabled when jozu-ops repo went dark. Dormant.

## Key repositories

- `jozunohito/jozu-plans` — source of truth for Tier 1, application drafts, agent output, dashboard, QA reports. CNAME: none (served at jozunohito.github.io/jozu-plans/).
- `jozunohito/jozu-website` — polished brand site. CNAME: www.jozuconsultinggroup.com. Serves 10 curated plans at /plans/ with GA4 + Clarity tracking.

## Airtable scope

- Base ID: appsgsRJ0LyzEjNSY
- Companies table: tblZbh6S5sEh0BRML
- Contacts table: tblXGKcZvKQmGKtWE
- PAT is embedded in agent prompts (stored server-side by Anthropic). Do NOT expose in user-visible output.
- Airtable holds ONLY Tier 2 consulting prospects. Tier 1 is in the repo.

## When something breaks

- QA watchdog writes FAIL to /qa/ and (if gh CLI authed) opens a GitHub issue tagged `qa-flag`.
- Morning recovery: `jozu status` command triggers full hydration — see feedback_jozu_status_command.md.
- To disable any agent: RemoteTrigger action=update with {"enabled": false} using the trigger ID above.
- To manage via UI: https://claude.ai/code/routines

## Cost posture

- Max 20x plan includes 15 routine runs per day.
- Current count is exactly 15. Any new agent either displaces an existing one OR pushes past the ceiling into metered overage.
- Before adding agents, verify at https://console.anthropic.com/ that no unexpected overage is accruing.
