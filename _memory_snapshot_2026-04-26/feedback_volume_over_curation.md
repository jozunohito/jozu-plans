---
name: Volume over curation — top 200 not top 15
description: Jeff 2026-04-24. He decides what's relevant, not me. Surface the full ranked list, not a curated short list.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

When summarizing pipeline output for Jeff, default to **top 200 ranked**, not top 5 or top 15.

Jeff explicitly said: "I don't want top 15. I want top 200."

His reasoning: I do not have authority to filter his pipeline down to a "manageable" curated subset. The agents do verification. Jeff does decision. My job is to RANK and DEDUP and surface comprehensively. His job is to pick.

## How to apply

When he runs `jozu status` after a batch of agents complete, the standard report is:

1. Recovery hydration as defined in `feedback_jozu_status_command.md`
2. **Ranked top 200 across all batches** (or all available verified roles if fewer than 200 exist), with:
   - Dedup against already-submitted set
   - Dedup across batches (same role surfaced by multiple agents → list once)
   - Honest fit score from each agent
   - Ceiling-flag column (in / over / under)
   - Apply-URL column (already verified HTTP 200 by the source agent)
   - Vertical column for filter
   - Geographic / location column

Order ranking by combined fit score + apply-priority, not by "what I think Jeff cares about."

Surface format that works: a single big markdown table he can scan, with sub-sections by vertical or geo for navigation. Total row count: aim for 150-250.

## What this rule prevents

- Me filtering "obvious" matches and hiding interesting outliers Jeff would have wanted to see
- Me putting only 5-10 picks in front of him and getting yelled at for it
- Me deciding what's "small enough" — that's not my call

## When summarization is appropriate

- Quick verbal callouts in chat (top 3-5 to highlight, with link to the full ranked file)
- Always paired with the full file path so Jeff can scan the rest at his own pace

## Source

Jeff 2026-04-24, after I had been surfacing "top 5 / top 10" repeatedly across 9 agent completions. He wants the volume.
