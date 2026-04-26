---
name: Capture every application status update Jeff mentions IMMEDIATELY
description: Locked 2026-04-25 evening. Whenever Jeff mentions any company name in passing as applied / declined / interviewed / paused / accepted, log it to applications_log.md in the same turn. Do not wait for him to ask.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

**When Jeff mentions any application status update in passing, capture it to `tier1/applications_log.md` IMMEDIATELY in the same turn.**

This includes:
- "I applied to X" — log as Submitted
- "X declined me" / "X passed" — log as Declined with date
- "X reached out for an interview" — log status update
- "I interviewed at X" — log status update
- "X gave me an offer" — log status update with terms
- "I'm pausing X" — log status update

Do not wait for Jeff to instruct "log it." Treat the mention as the instruction.

## Why this matters

If a company is not in the applications log, I cannot deduplicate it from future role surfacing. Re-surfacing a declined role to Jeff exposes a memory-hygiene failure and burns his time + my credibility.

## Specific failure 2026-04-25

Jeff told me StackOne declined Friday morning 2026-04-24. I never captured that signal into the applications log. On 2026-04-25 evening, the K5 agent surfaced StackOne as a fresh "apply this week" pick, which I then forwarded to Jeff. He correctly called this out as a hygiene failure.

The fix: every Jeff-mentioned status update gets logged in the same turn. No deferral.

## Operational discipline

When the user message contains ANY of these patterns:
- "applied to [Company]" / "submitted to [Company]" / "I applied [Company]" — log
- "[Company] declined" / "[Company] passed on me" / "[Company] said no" / "rejected" — log
- "[Company] reached out" / "[Company] wants to interview" / "[Company] booked a call" — log
- "[Company] gave me an offer" / "[Company] offered" — log
- "I'm pausing [Company]" / "skip [Company]" / "[Company] is dead" / "[Company] is gone" — log to mock-list or status update

I edit `tier1/applications_log.md` in the same response. Tight log entry. No analysis required at log time; the analysis (e.g., post-mortem) is a separate motion.

## Source

Jeff Aragon 2026-04-25, after I re-surfaced StackOne despite his Friday-morning notice that StackOne had declined: "stack one declined yesterday. deploy an agent to figure out why. are you keeping a log of all of these? You should have already known that Stackone was a decline. I told you this friday morning."

He is right. Lock the rule.
