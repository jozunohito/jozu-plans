---
name: Morning recovery command — "jozu status"
description: Jeff's standard session-start command. Triggers a deterministic hydration sequence before engaging in new work.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

When Jeff opens a new session with any of these triggers, immediately run the recovery sequence below BEFORE engaging in any new work or conversation:

- `jozu status`
- `morning`
- `catch me up`
- `morning brief`
- `what happened`
- `status`
- `hydrate`

## The recovery sequence

1. Read today's session log at `C:\Users\Jeff\claude-projects\sessions\YYYY-MM-DD_session.md`. If today's does not exist, read the most recent prior day's log.
2. Read from the jozu-plans repo (clone if not present; it lives at `C:\Users\Jeff\claude-projects\jozu-plans\` locally):
   - `/qa/LATEST.md` — overnight watchdog status (PASS / WARN / FAIL)
   - `/applications/pipeline_log.md` — applications drafted, pending submission, submitted
   - `/dashboard.html` — current Jozu Score and trending data
   - `/airtable_feed_architecture.md` — if architecture reconfirmation needed
3. Run `git log --oneline -20` in both jozu-plans and jozu-website to see overnight agent commits
4. Compile a report in under 300 words:
   - Agent runs overnight (counts, successes, failures)
   - Applications ready to submit (by company + role, with location of draft files)
   - New warm signals (StackOne-type plan visitors, signal-agent trigger events, Plausible/GA hot visitors)
   - QA flags (any FAIL or WARN from the watchdog)
   - Top 3 actions for Jeff today
5. Hand control back with "what first?"

## Why

Jeff has 8 scheduled agents running overnight. He needs a deterministic way to hydrate context each morning without re-explaining anything. This rule makes recovery a single command regardless of which Claude session instance he lands in. The conversation history may be gone but the repo state, QA reports, and session logs persist.

## How to apply

- Treat the command triggers above as equivalent. Do not ask Jeff "which report do you want?" Just run the sequence.
- If any of the expected files are missing (e.g., QA report stale or absent), flag it explicitly in the report — that itself is a signal about agent health.
- Keep the report under 300 words. Jeff reads it first thing in the morning, often before coffee.
- After the report, wait for Jeff's instruction. Do not propose next actions within the report — those are decisions he makes after reading.

## Recovery limitations to be honest about

- I cannot recover conversation history from a prior session. Only durable artifacts (files, commits, memory files) transfer.
- If Jeff asks about a conversational detail from the prior session that wasn't written to a file, I must say "that was conversational only, not persisted — tell me what you remember and we reconcile."
- Memory rules persist but are subject to truncation past 200 lines in MEMORY.md; keep entries tight.
