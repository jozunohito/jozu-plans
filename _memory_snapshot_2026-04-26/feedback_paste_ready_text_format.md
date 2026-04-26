---
name: Paste-ready text format — contiguous paragraphs, no hard wrapping
description: Locked 2026-04-25. When delivering text Jeff will paste into an external system (application form, cover letter box, email body), use contiguous paragraphs with no internal line breaks.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

When delivering ANY text Jeff will paste into an external system — application form text boxes, "tell us more" fields, cover letter bodies, email bodies, LinkedIn message boxes, anywhere — format it as **contiguous paragraphs with no internal hard line breaks**, separated by blank lines between paragraphs.

**DO:**
- Wrap the deliverable in a single code block (` ``` `) so whitespace is preserved exactly
- Write each paragraph as one long continuous line — let the destination text box wrap naturally
- Use a single blank line between paragraphs
- Keep punctuation and capitalization clean for direct paste

**DO NOT:**
- Hard-wrap text to ~60 or 80 characters per line. This forces Jeff to manually reformat every paste, costing 10-15 minutes per application.
- Add bullets, headers, or markdown formatting unless the destination explicitly supports markdown (rare for ATS forms)
- Use single line breaks within paragraphs to "look pretty" — the destination box treats single line breaks as paragraph breaks usually, causing visual fragmentation

## Why this matters

Jeff pastes Claude-generated text into:
- Greenhouse / Ashby / Lever / Workable application form text boxes
- BuiltIn / LinkedIn application forms
- Email clients (Gmail, Outlook)
- LinkedIn message boxes
- Direct cover-letter-paste fields

Every one of these renders text differently. Hard-wrapped lines from a 60-char code block paste as ragged broken lines that Jeff has to manually fix one paragraph at a time. Contiguous paragraphs paste cleanly because the destination text box owns the line wrapping.

## When the rule does not apply

- Markdown source files (resume `.md`, plan `.md`) — those are written for pandoc-to-DOCX rendering and use whatever formatting that toolchain expects
- README / documentation files — markdown formatting OK
- Tables, structured data — keep table formatting
- Code samples — code blocks preserve formatting

The rule only applies when Jeff is going to **paste prose into an external box**.

## Source

Jeff 2026-04-25, after multiple cover letter and form-answer deliveries: "you keep formatting in small bunched up sections left justified, and then I have to unfurl this in a window. Very awkward. I want text contiguous, with spaces as needed so I don't have to fix and spend 15 min editing each window. get this better."
