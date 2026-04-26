---
name: Earlier Career section — default-exclude across all resume variants, gate-triggered re-include only
description: Locked 2026-04-25. Earlier Career stays in master MD as source of truth but is removed from all DOCX outputs by default. Three named gates trigger per-submission re-inclusion.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

**Earlier Career section is REMOVED from the default DOCX output of every resume variant** (VP Sales, CRO master, Vanta, any future variant).

**The master `.md` files retain every Earlier Career fact** as source of truth. Nothing is deleted from `career_facts.md` or the resume MD bodies. The exclusion happens at the DOCX-render level only — when a submission triggers a gate, we re-add the relevant subset to the MD before regenerating the DOCX.

## Why default-exclude (first principles)

Recruiter eye-tracking studies (Ladders 2012/2018, ResumeGo 2023): Pass-1 screen is 6-8 seconds, fixates on six fields (name, current title, current company, dates, previous title/company, education). Pass-2 hiring-manager review is 60-180 seconds with strong recency bias toward roles in the last 7-9 years.

Resume-length data (ResumeGo 2023, n=600+ recruiters): at equal content quality, 2-page resumes received 22% fewer interview callbacks than 1-page resumes for senior IC and player-coach roles. The penalty is largest when page 2 contains older content.

Jeff's load-bearing record covers Dec 2012 to present (Jozu, Insightin, Ushur, UKG, CDK, OnShift, plus the 12-year concurrent CCS Coach track). That is 13+ years of recent and relevant material. Earlier Career roles ended ~15 years ago. They sit at the bottom of a 2nd page, in the lowest-attention zone, competing with the recent record for finite reader attention.

## What Earlier Career contributes when it does

Three discrete signals, each gate-triggered:

1. **AT&T** — 5 years selling AT&T security portfolio + Global WAN. Cyber/networking depth + F500 multinational scale.
2. **Time T.I. Tokyo** — 4 years teaching the Harvard Negotiation Project. Cross-cultural enterprise selling + nemawashi/ringi fluency.
3. **True Merchant Services + ABC, Inc.** — Co-Founder/CEO of 35-seller org + 50-employee branch P&L. Leadership-at-scale credentials.

## The three gates that trigger re-inclusion

Per submission, evaluate against these gates BEFORE regenerating the DOCX:

| Gate | Trigger | Action |
|---|---|---|
| **AT&T gate** | Role involves cyber, security, networking, WAN, managed services, F500 multinational infrastructure procurement | Re-include AT&T section. Optionally add a one-line phrase to the Summary referencing the AT&T security/WAN foundation. |
| **Time T.I. gate** | Role is at a Japanese-HQ company, OR involves APAC market entry, OR explicitly wants cross-cultural enterprise-buyer fluency | Re-include Time T.I. section. (Note: Summary already mentions Tokyo HNP; sometimes the Summary line alone is enough.) |
| **Leadership-scale gate** | Role explicitly requires prior leadership at scale (50+ people, multi-year P&L), AND post-2012 record does not assert it loudly enough. Miro-tier T2 CRO seats and over-head Tier 1 founding seats with explicit "show me you've led big orgs before" language. | Re-include True Merchant + ABC. Optionally add a one-line phrase to the Summary asserting the leadership track. |

Two gates can fire together (e.g., Japanese cyber co triggers AT&T + Time T.I.). Re-include both subsets in their original chronological order.

## Workflow per submission

1. Read the role description against the three gates.
2. If no gate fires: render DOCX from the default master MD (Earlier Career excluded). Done.
3. If one or more gates fire: temporarily add the relevant Earlier Career subsection back to a per-submission copy of the MD, regenerate DOCX from that copy, save the resulting DOCX in the per-submission application folder. The master MD remains in default-exclude state.
4. Optionally adjust the Summary paragraph to absorb a one-line reference to the gate-triggered signal at the highest-attention top-of-resume position.

## What this rule prevents (and what it does not)

**Prevents:** length-tax + attention-dilution on the 60-70% of applications where Earlier Career adds no value.

**Does not prevent:** the gate-triggered 30-40% of applications from getting the relevant signal — the rule explicitly handles that case via per-submission re-inclusion.

**Critically does NOT enable:** bastardization. Every fact in Earlier Career stays in the master MD as truth-of-record. The rule governs which true facts surface in which submission. That is curation. Curation is not bastardization. Bastardization (rewriting bullets, fabricating outcomes, inflating tenures, claiming capabilities that do not exist) remains a hard-violation of APEX truth and is forbidden regardless of any tailoring rule.

## Source

Jeff Aragon 2026-04-25, after multi-message reasoning on resume length, recruiter attention, and the "purist state" he wants to maintain. Verbatim direction: "We should talk about as much as necessary in the intro paragraph, leave earlier career off of these variants - all variants - unless it specifically makes sense to add it back in."

## Canonical filenames (locked 2026-04-25 evening)

After Earlier Career removal + 0.5" top margin adjustment by Jeff:

- **VP Sales trimmed (DEFAULT for founding-tier and sub-CRO submissions):** `C:\Users\Jeff\claude-projects\resume\jeff_aragon_resume_vp_sales_tri.docx`
- The `_tri` suffix is intentionally cryptic — Jeff does not want recruiters reading "trimmed" in metadata or filenames. We know it; they don't.
- **CRO master:** `C:\Users\Jeff\claude-projects\resume\jeff_aragon_resume.docx` (also Earlier Career trimmed per the rule).
- **Master MDs retain ALL Earlier Career facts** for gate-triggered re-inclusion. Master MDs are: `jeff_aragon_resume.md`, `jeff_aragon_resume_vp_sales.md`, `jeff_aragon_resume_vanta.md`.
