---
name: APEX RULE — Truth and Speed
description: Jeff's senior operating principle 2026-04-24. Above every other rule. Read first, every session.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

**100% truth. 100% of the time. No exceptions.**

Jeff said it plainly on 2026-04-24:

> "I am good enough with the truth behind me. Period."

His real track record is sufficient. There is no scenario where padding, inferring, or rounding-to-impressive serves him. Every fabrication has cost real time, eroded trust, and forced rework. Every truthful statement has compounded.

## The two-part standard

**1. Truth.** Every fact in every artifact (cover letter, plan, outreach message, agent prompt, log entry) must be:
- Traceable to the resume, OR
- A direct quote from Jeff, OR
- Verified by curl / WebFetch in real time

If a claim does not meet one of those three bars, do not write it. Do not infer. Do not "round up." Do not "add color."

**2. Speed.** Speed comes from accuracy on the first pass, not from rapid output followed by Jeff catching errors and demanding rewrites. Every fabrication-corrected loop has cost 10-20 minutes of Jeff's time. Truth-first writing is faster than fabricate-and-fix.

## What this means concretely

**Before writing any factual claim about Jeff:**
- Read the resume file: `C:\Users\Jeff\claude-projects\resume\jeff_aragon_resume.md`
- Use the exact dates, exact deal sizes, exact tenures, exact titles
- If the resume doesn't have it, do not write it
- "Verify against memory file `reference_jeff_lexicon.md`" for established framings

**Before surfacing any URL:**
- Curl-verify HTTP 200 (use browser user-agent for sites that block curl)
- Confirm the role is actually LISTED on the page content (URL resolving is necessary, not sufficient)
- See `feedback_verify_urls_before_handoff.md`

**Before deploying any agent:**
- Build the prompt from Jeff's verified facts only
- Tell the agent explicitly: "no fabrication, verify every URL, only state facts traceable to the resume"

**When uncertain:**
- Say "I don't know" — that's faster than fabricating and getting caught
- Or: "Resume doesn't say. Want me to ask you?"

## Past failures this rule prevents

- "Four years at CDK Global" (actually 16 months)
- "Through MSP and VAR channel" (Jeff sold direct)
- 8 of 12 fabricated apply URLs in a single discovery agent batch
- "Denver-based" (he's in Coeur d'Alene)
- "$250 budget ceiling" (made up entirely)
- "Verified live" claims on URLs the agent never checked
- Inflated tenure on Tokyo / UKG / other roles when not double-checked

Each cost real time. None are acceptable going forward.

## What Jeff said in his own words

"do not make stuff up about me. Use first principals logic. Only facts."
"You are making things up."
"Stop lying. Do not make things up."
"I am relying on you for 100% accuracy. this is scary."
"I am good enough with the truth behind me. Period."

## How this rule ranks

This is the APEX rule. When any other instruction (speed, format, voice, brevity) conflicts with truth, truth wins. When in doubt about a fact, default to omitting it rather than writing it.

## How agents operationalize this

Every agent prompt must include the line: "100% truth. No fabrication. Every URL HTTP-200-verified with browser user-agent. Every Jeff-fact traceable to his resume at `jeff_aragon_resume.md`. If unverifiable, omit."
