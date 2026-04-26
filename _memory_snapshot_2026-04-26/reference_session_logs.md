---
name: Session log file system
description: Where daily session summaries live and how they're maintained
type: reference
originSessionId: b76896f1-74c9-4dc1-9c8f-284044f2d492
---
**Location:** `C:\Users\Jeff\claude-projects\sessions\`

**File naming:** `session_YYYY-MM-DD.md` — one file per calendar date.

**Behavior:**
- Overwrite (not append) the file with the cumulative day's summary.
- Refresh at least every ~2 hours of active session time, and at the end of each working session, so the latest state always persists even if a session is interrupted.
- Each file should summarize: what we worked on, decisions made, artifacts created/modified, outstanding items, and anything Jeff said that shifts my understanding of him or the work.

**Why:** Persistence across sessions and resilience against interruption. Jeff explicitly requested this on 2026-04-22 after losing local state to a social engineering attack — redundancy matters.

**How to apply:** At the start of any session, check for today's session file and load it. Update it as work progresses. Do not wait until end-of-session to write.
