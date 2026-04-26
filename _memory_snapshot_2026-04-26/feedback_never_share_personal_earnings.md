---
name: Never share Jeff's personal earnings or commissions externally
description: Hard rule. Personal earnings and commission figures are internal-only context, never appear in applicant-facing documents
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

**Never include in any external-facing document:**
- $1M+ IC earnings year (any phrasing: "$1M personal earnings", "$1M+ in earnings", "top-tier IC compensation", etc.)
- $418K largest single commission (any phrasing, any amount)
- Any specific personal income, commission, or bonus figure

This applies to:
- Resumes (master and any tailored variant)
- Cover letters
- 90-day plans
- Mentor one-pagers
- LinkedIn messages
- Outreach emails
- Any document Jeff sends to an employer, client, partner, VC, recruiter, or headhunter

**Why:** These figures are Jeff's personal compensation. Hiring managers care about what Jeff generated for the business, not what he took home. Sharing earnings makes him look mercenary, diminishes the operating achievement that stands next to the figure, and invites comparison he did not ask for.

**Internal use is fine:** these figures inform how I understand Jeff's caliber and how I position him in my own framing. They stay in `career_facts.md` and in auto-memory for context. They never make it into an artifact that leaves his hands.

## What TO use instead (operating impact)

Lead with what Jeff generated for the business:
- $150M+ attributed career revenue
- $8M ARR and $24M TCV in under two years at Series A Ushur
- Largest deal in company history, ~$10M TCV
- 10x peer outperformance at Ushur
- Top 5 percent globally at UKG for 5.5 years
- 25+ President's Club and Sales Excellence Awards
- Multiple Legend Makers awards at UKG

## How to apply

Before writing any Jeff-facing external artifact, scan for:
- "$1M" — drop it
- "$418K" — drop it
- "largest single commission" — drop it
- "personal earnings" — drop it
- "IC earnings" — drop the specific dollar figure; "senior IC" is fine as a role descriptor

If the draft contained either figure, rewrite to lead with an operating number ($24M TCV, $8M ARR, $10M largest deal, 10x peer outperformance).

## Pre-flight scrub procedure (ENFORCEMENT)

Triggered failure 2026-04-24: I built a tailored resume variant by copying from the master and missed the `$1M+ in personal earnings` line in Signature Results. Jeff caught it. "Choogy. Terrible. Must never appear again."

**Mandatory scrub before delivering ANY resume / cover letter / plan / outreach artifact:**

1. Run `Grep` against the artifact for the regex: `personal earnings|\$1M\+ in personal|\$1M in personal|\$418|largest single commission|in earnings as an individual contributor`
2. If ANY match returns, do not deliver. Edit out the offending line. Re-grep.
3. Apply this scrub to every variant when forking from a master (master might still carry the line — fork inherits the contagion).
4. Apply this scrub to ALL output formats — `.md`, `.docx`, `.html`, `.pdf`. Editing one file does not propagate to the others. Each must be independently checked or regenerated.

**Tailored-variant rule:** when building a new resume variant from an existing one, run the scrub on the SOURCE before forking, then on the new variant after editing, then on the regenerated DOCX/HTML. Three checkpoints minimum.

**Internal-only docs (career_facts.md, etc.) carry forbidden figures invisibly** — I read them as context for writing artifacts. Replace internal-doc figures with explicit "DO NOT EXTERNALIZE" guard text so the rule is visible in the source I'm reading from.
