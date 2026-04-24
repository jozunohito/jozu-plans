# Airtable Feed Architecture

**Last updated:** 2026-04-24 by Claude (overnight session)
**Purpose:** Clear plan for what goes in Airtable, what does not, and which agent writes which rows.

---

## The rule

**Airtable is RGI's operating surface.** It holds Jozu consulting prospects that RGI sequences for outbound (LinkedIn + email + phone). Nothing else.

**Tier 1 (Jeff's personal role applications) does NOT live in Airtable.** Tier 1 lives in this repo under `/tier1/inbox/` and `/tier1/applied/`.

---

## What Airtable holds

| Status | Meaning | Owner |
|--------|---------|-------|
| `RGI_QUEUE` | Ready for RGI enrichment + outreach | RGI |
| `RGI_IN_SEQUENCE` | Active outbound in progress | RGI |
| `PLAN_PENDING` | Personalized plan being drafted, hold outbound | Jeff |
| `RESPONDED` | Prospect replied, check Responses table | RGI |
| `JEFF_HANDOFF` | Qualified — Jeff takes it | Jeff |
| `NURTURE_90D` | Recycle in 90 days | RGI |
| `CLOSED` | Dead for now | RGI |
| `JEFF_MANUAL` | Strategic/premium prospect, Jeff works directly | Jeff |

**Segments (for Jozu consulting prospects only):**
- A = Japan / APAC to US bridge (premium; Jozu Japan-US Market Entry Sprint fit)
- B = AI / ML
- C = Fintech
- D = Healthtech
- E = Cybersecurity
- F = Enterprise SaaS / Dev tools
- G = Other verticals
- H = YC recent batch
- I = **DEPRECATED** (was Tier 1 role targets; now live in `/tier1/` repo folder)

---

## Which agent writes which rows

| Agent | Writes to | Tier | What it creates |
|-------|-----------|------|-----------------|
| `jozu-role-search` | Airtable (Tier 2 only) + `/tier1/inbox/` (Tier 1) | Both | Adds Tier 1 role files to repo, adds Tier 2 prospects to Airtable as `RGI_QUEUE` or `JEFF_MANUAL` |
| `jozu-apac-sourcing` | Airtable (Tier 2 only) + `/tier1/inbox/` (Tier 1) | Both | Same as above, APAC-native-language sources |
| `jozu-emea-sourcing` | Airtable (Tier 2 only) + `/tier1/inbox/` (Tier 1) | Both | Same as above, EMEA-native-language sources |
| `jozu-signals` | Airtable (PATCH Trigger Signal field) | Tier 2 | Enriches existing Tier 2 rows with trigger events |
| `jozu-qa-watchdog` | `/qa/` reports + GitHub issues | Both | Validates sourcing agents wrote to correct places |
| `jozu-rfp-fed-intel` | `/intel/jozu-rfp-fed-intel/` | Tier 1 adjacent | Federal/JETRO/accelerator RFPs; Jeff reviews, bids manually |
| `jozu-application-drafter` | `/applications/` | Tier 1 | Drafts cover letter + resume bullets for each Tier 1 plan |
| `jozu-warm-network` | Airtable (PATCH) + `/warm_network/` reports | Tier 2 | Flags warm LinkedIn paths on Tier 2 rows |
| `jozu-networking-events` | `/events/` | Both | Events where Jeff can meet role contacts + Jozu prospects |

---

## What Jeff does manually

- Approve Tier 1 roles from `/tier1/inbox/` by moving them to `/tier1/approved/` (application-drafter picks up from approved)
- Review RGI weekly disposition log (`logs/weekly_disposition.md` in jozu-outreach repo) every Friday
- Move RGI_IN_SEQUENCE rows to JEFF_HANDOFF when a qualified reply arrives
- Update PLAN_PENDING rows to RGI_QUEUE when plan goes live (with Plan URL populated)
- Add strategic prospects as JEFF_MANUAL with his own signal

## What RGI does (from the outreach email V2)

- Pull `RGI_QUEUE` rows, enrich with contacts, send LinkedIn/email/phone sequences
- Log every touch in Sequence Touches table
- Log responses in Responses table
- Tag Jeff on qualified replies, move to `JEFF_HANDOFF`
- Stand up warmed shadow domains for email outbound (jozu-consulting.com, jozuconsultinggroup.io, getjozu.com)
- Run max connection requests + InMails on Jeff's and Meag's LinkedIn profiles

---

## Why this architecture

1. **Separation of ownership.** RGI works Airtable; Jeff works `/tier1/`. Neither steps on the other.
2. **Privacy.** Tier 1 is Jeff's personal job search. It doesn't need to be visible to RGI or to anyone else with Airtable access.
3. **Different data shapes.** Tier 1 files need the full plan context + fit analysis. Tier 2 rows need short structured fields for sequence automation.
4. **Disaster recovery.** Tier 1 in git = version controlled, durable across machine wipes. Airtable is its own cloud. Both survive independently.

---

## Open questions for Jeff to decide

1. Should Tier 1 roles also be tracked in a spreadsheet / dashboard for Jeff's own progress view? (Proposal: dashboard.html pulls from `/tier1/` and shows submitted vs open.)
2. Should RGI be given any `/tier1/` read access for occasional "did Jeff apply to this yet?" lookups? (Probably not — keep walled off.)
3. When Jeff gets his first consulting client, where does their operational data live? (New Airtable table? Separate client workspace? Decide when it happens.)

---

## Change log

- 2026-04-24: Initial architecture document. Corrects prior confusion where `jozu-role-search` was writing Tier 1 to Airtable as JEFF_MANUAL/Segment I. Jeff's clarification: Tier 1 is his alone, not RGI's business. Agents updated to write Tier 1 to `/tier1/inbox/` in this repo instead.
