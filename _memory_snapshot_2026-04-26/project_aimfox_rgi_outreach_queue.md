---
name: Aimfox / RGI LinkedIn outreach queue (Airtable-fed) for Jeff's applied-to companies
description: Locked 2026-04-25 evening. Every role Jeff applies to gets 1-3 leader-level LinkedIn connection requests with manually confirmed tailored notes. Claude maintains an Airtable table that RGI processes every few hours via Aimfox. This is Jeff's role-search outreach automation, separate from Jozu/Kimi work.
type: project
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---

## The mandate

For every role Jeff applies to (and every role we confirm has been submitted), Claude:
1. Identifies 1-3 senior-leader contacts at the company (CEO, Founder, Head of Sales, COO, CTO, hiring manager — whoever is the right altitude for the seat)
2. Confirms each target's LinkedIn URL is the correct live profile. **Never queue an unverified LinkedIn URL.** If the URL cannot be confirmed, the row does not get added until Jeff verifies in his logged-in session.
3. Writes the connection note using Jeff's locked voice template (see "Voice template" below).
4. Surfaces the row(s) to Jeff for sign-off in the same conversation.
5. On Jeff's approval, appends the row(s) to the Airtable queue (or to the staging CSV at `tier1\aimfox_queue_staging.csv` until Airtable write-access is wired).
6. RGI runs Aimfox every few hours, fires the connection requests from Jeff's LinkedIn, and writes Sent / Connected / Replied status back into the table.
7. **RGI reports back to Jeff when someone accepts the connection.** This is the trigger for Jeff's follow-on motion (DM the new connection with the plan-tease, schedule a call, etc.).

## Voice template — LOCKED, Jeff's voice, never AI cadence

**Default base template (use as written, only personalize the bracketed fields):**

```
Hello [First name], I have submitted to the [Role title] role on your website and have built a 90-day plan I'd love to review with you. I am looking forward to connecting. Thank you, Jeff
```

Personalization fields:
- `[First name]` — target's first name only (never "Mr. / Ms.", never full name, never title)
- `[Role title]` — the role title as it appears on the company's careers page (mirror their language, do not invent a punchier title)

Character count: ~165-220 depending on role-title length. Fits inside LinkedIn's 300-char cap on free and Premium accounts. Aimfox is run on a Premium account to bypass the 5-note-per-month free-tier cap.

## What Jeff's voice IS

- Polite. Respectful. Direct.
- Plan-tease (90-day plan) is the opener of value, not "worth a call?" "quick chat?" or any other shortened AI phrase.
- "I'd love to review with you" — natural, warm, contracted English.
- "I am looking forward to connecting" — committed, not "would love to connect."
- "Thank you, Jeff" — always closes this way.

## What Jeff's voice IS NOT (auto-reject any draft that includes these)

- "Worth a call?" — banned.
- "Quick 15 min?" — banned.
- "Got 10 minutes?" — banned.
- "Hop on a call" — banned.
- "Pick your brain" — banned.
- "Synergies / leverage / unlock value" — banned (corporate AI-cadence words).
- Em dashes — banned (existing voice rule).
- "Hey [Name]" openers — banned. Always "Hello."
- "Best, / Cheers, / Regards," sign-offs — banned. Always "Thank you, Jeff."

## When the default template does NOT fit (rare — surface to Jeff for one-off)

Cases where the locked default needs adjustment:
- Role was posted ONLY on Greenhouse / Lever / Ashby (not on the company's own website). Substitute "on your website" → "at [Company]". Surface to Jeff before send.
- Target is NOT the CEO / Founder but a Head of People / hiring manager (different altitude). Surface to Jeff for a one-off polite-but-different draft.
- Jeff already applied to a different role at the same company. Surface for a re-craft so the second target sees something fresh.
- Jeff has a personal connection to the target (mutual contact, prior conversation). Surface for handcraft.

In all these cases, never silently regenerate. The locked template is the default; everything else is Jeff-approved one-offs.

## Operating principle

We do not annoy. We do not look like AI. The plan-tease IS the value signal. The note is short on purpose so the reader has room to be curious — not because curiosity has been engineered out of an AI-generic phrase. Jeff's track record speaks once the prospect connects; the note's only job is to earn the connection.

## Why this exists

LinkedIn connection requests with a tailored note land at far higher accept rates than templated spam. Jeff's track record demands the note be specific to the company / leader / role. RGI has the throughput tool (Aimfox); Claude has the context to write the note. Airtable is the contract surface between the two.

This is separate from Kimi's Jozu outreach work. Kimi runs the Jozu side of Airtable. Claude owns this Aimfox queue table for Jeff's personal role search.

## Airtable table — proposed schema

**Table name:** `aimfox_outreach_queue` (working name; confirm with Jeff before creation)

**Required fields:**

| Field | Type | Notes |
|---|---|---|
| Application ID | Autonumber | Primary key |
| Company | Single line text | Required |
| Role applied | Single line text | Required |
| Application URL | URL | Direct apply link (verify live) |
| Application date | Date | When Jeff submitted |
| Target name | Single line text | Required (CEO, Founder, etc.) |
| Target title | Single line text | Required |
| Target LinkedIn URL | URL | Required — Aimfox keys off this |
| Sender identity | Single select | Always Jeff. Field kept for audit only. |
| Connection note | Long text (≤300 char) | Manually confirmed, never templated |
| Note approved by Jeff | Checkbox | Aimfox only fires when TRUE |
| Status | Single select | Queued / Sent / Connected / Replied / Skipped / Withdrawn |
| Date sent | Date | RGI / Aimfox writes back |
| Date connected | Date | RGI / Aimfox writes back |
| Reply received | Long text | RGI / Aimfox writes back |
| Priority | Single select | High / Med / Low |
| Notes for RGI | Long text | Special instructions, do-not-mention items |
| Created | Created time | Automatic |
| Created by | Single line text | "Claude" — Claude writes this column |

**Hard rules baked into the schema:**
- LinkedIn connection notes max out at 300 characters. Note field has a character counter. If note > 300, the note must be re-drafted before approval.
- Aimfox only fires rows where `Status = Queued` AND `Note approved by Jeff = TRUE`. This is the safety gate against accidental sends.
- Unique constraint on `Target LinkedIn URL` — never queue the same person twice. If Jeff applies to two roles at the same company, second-application connection notes go to a different leader.
- 1st-degree connections route differently: connection request becomes a direct message. Schema needs a `Connection degree` field (1st / 2nd / 3rd / Unknown) so RGI knows whether Aimfox sends a connect or a DM.

## Sender identity — locked

**Always Jeff.** Aimfox runs Jeff's LinkedIn account. Connection note is first-person from Jeff. ("Hello [Name], I applied for the Head of Sales role at Lovable yesterday and will welcome a chance to connect.") RGI is the operational vendor that runs Aimfox against Jeff's LinkedIn session, spaces the sends to avoid LinkedIn trip-wires, and writes status back into the queue.

**Bill Canady is NOT in this architecture.** Bill runs his own consulting practice + other businesses. RGI is Bill's vendor for top-of-funnel into Bill's practice. Jeff is a closer for Bill at the 80/20 Institute (subject to change if Bill does not generate intro calls). That commercial relationship is fully separate from Jeff's role-search outreach. Bill does NOT refer Jeff for jobs and does NOT appear as a sender in any connection note.

RGI is a multi-purpose vendor:
- For Bill: Bill's top-of-funnel pipeline.
- For Jeff (this queue): Aimfox automation on Jeff's job applications, sending FROM Jeff's LinkedIn account.

## Workflow when Jeff confirms an application

The same turn Jeff says "applied to [Company]":
1. Log to `tier1/applications_log.md` (existing locked rule, not optional).
2. Identify the 1-3 target leaders. Default target priority:
   - CEO / Founder / Co-Founder
   - Head of Sales / VP Sales / CRO if one exists (likely will not — that is the seat Jeff applied for)
   - COO or CRO-equivalent
   - Hiring manager named in the JD if known
3. **CONFIRM each target's LinkedIn URL.** Pull from a verifiable public source (company team page, Crunchbase founder profile, public Google result that points to a reachable LinkedIn profile). If the URL cannot be confirmed, mark the row "VERIFY ON LINKEDIN" and surface to Jeff to confirm in his logged-in session before the row is queued. Never fabricate a LinkedIn URL.
4. **Generate the connection note using the locked voice template** (above). The note is NOT custom-crafted per company — it IS the locked template with the target's first name and the role title slotted in. The plan-tease is the differentiator. Anything beyond the template is a one-off and gets a Jeff-approved handcraft.
5. Surface row(s) to Jeff for sign-off (verify name, title, LinkedIn URL, role, company are all correct).
6. On approval, append rows to the dedicated Airtable base "Jeff Role Search Outreach" (when wired; until then, append to the staging CSV at `tier1\aimfox_queue_staging.csv` for Jeff to import into Airtable manually).
7. RGI processes the queue every few hours via Aimfox. Aimfox writes back Sent / Connected / Replied. RGI reports back to Jeff each time someone accepts a connection — that is Jeff's signal to start the follow-on motion.

## Throttle awareness

LinkedIn enforces ~100 connection requests / week safely on Free; Aimfox spaces them to avoid trip-wires. RGI runs the queue every few hours. Practical implication: if Claude pushes 5 applications a day, that is 10-15 new queue rows / day, and RGI's Aimfox will pace them across the week. Do not flood the queue with 50 rows in one push.

## Dedup discipline

- Never queue the same `Target LinkedIn URL` twice across all applications.
- Never queue Jeff's existing 1st-degree connections as connect requests (different motion = direct message).
- Never queue someone Jeff has already DM'd in the last 90 days from his own account.
- Always check the queue's existing rows before adding new ones.

## Coordination with Kimi and with Bill's funnel (three streams stay separate)

This queue is Jeff's role-search outreach ONLY. Three streams are kept clean:
1. **This queue (Claude-operated):** Jeff's job-search LinkedIn connection requests. Sender = Jeff.
2. **Jozu / Kimi outreach:** Kimi runs Jozu's prospecting. Different Airtable structure. Sender = Jeff (as Jozu CRO + Founder).
3. **Bill Canady's funnel (RGI-operated for Bill):** Bill's top-of-funnel for his own practice. Different audience, different LinkedIn account, different motion. Claude does NOT touch this. Kimi does NOT touch this. Jeff's role with Bill is closer-only.

Crossover discipline:
- If a target leader at a company Jeff applied to is ALSO a viable Jozu prospect, Kimi handles the Jozu follow-on AFTER the role-search connection lands — never both in the same note.
- Bill's commercial leads NEVER appear in this queue or in Kimi's Jozu queue.

## Recommended Airtable architecture

**New dedicated base** named "Jeff Role Search Outreach," scoped only to this queue. Keeps the three streams cleanly separated. Different LinkedIn accounts, different audiences, different motions — different bases.

## Source

Jeff Aragon 2026-04-25 evening: tech stack update + new operational mandate.

> "I also own Folk CRM (you helped me select and set it up). I also own Apollo. We do not use airtable as a CRM. We use Airtable as a collaboration hub for Jeff and RGI to work together... a tool that Kimi will be deployed to operate from now on for Jozu work, and Claude's work will be to use Airtable to feed only highly tailored CSV with exact, manually confirmed Intro language to CEO's and other leaders of firms we've applied to (all of them will get connection requests with a tailored note, and this will be fed to RGI nightly through airtable... they can run a routine every few hours to automate linkedin outreach to that group via their toolset (Aimfox is the tool)."

Lock the workflow. Build the table. Operate it on every confirmed application.
