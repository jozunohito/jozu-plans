---
name: Unsolicited applications — decline is not signal
description: Rule for interpreting response (or non-response) to applications submitted without an active matching job posting. Different interpretive weight than solicited apps.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

**An unsolicited application is a submission where no specific role matching Jeff's profile is currently posted.** Jeff applied via a general "we're always interested" intake, a talent pool, a recruiter-only job, or a generic careers form.

**For unsolicited applications, a decline (or silence) is NOT a signal about fit.** It's a signal that the company is not hiring for this role right now. Do NOT read rejection as "Jeff's profile is wrong." Do NOT feed unsolicited declines into the filter logic, the cover letter language, or the positioning of future applications.

For contrast: a decline from a **solicited** application (Jeff applied against a real, posted, open role he matched) IS a signal worth reading — calibration input on fit, positioning, seniority, vertical, or geography.

## Why

Jeff applies proactively to companies that interest him even when no open role exists (example: Arbiter AI on 2026-04-24 — no sales opening, submitted through the generic "apply to work here" intake). The purpose is to land in the talent pool and be considered first when hiring reopens. The company may decline or never respond purely because there's no active slot, not because Jeff is a poor fit.

Reading unsolicited rejections as signal would:
- Cause false calibration (tuning the profile to address a non-existent problem)
- Erode confidence unnecessarily
- Miss the real insight: Jeff is in the pool for when they DO hire

## How to apply

**When tracking submissions in any log or tracker:**
- Tag each submission as SOLICITED or UNSOLICITED
- Tag the specific job URL if solicited
- Tag "general intake" or "talent pool" if unsolicited
- On decline, note the disposition but do NOT factor unsolicited declines into the filter / positioning / cover letter adjustments

**When Jeff asks "why didn't they respond?":**
- If unsolicited: "No active role — nothing to respond to. Normal."
- If solicited: then we analyze fit, positioning, competitive field, etc.

**When deploying rejection-analysis agents:**
- Only feed SOLICITED declines into the analysis
- Set UNSOLICITED declines aside as null data

## Example application

**2026-04-24 — Arbiter AI CRO:**
- Ashby URL returned HTTP 200 but role was not listed on Arbiter's own careers page
- Jeff submitted via generic application intake
- Status: UNSOLICITED. No signal on any future decline or silence.

## What this preserves

Jeff's mental energy. Jeff's accurate calibration. Jeff's willingness to continue sending unsolicited applications at companies of interest without taking silence personally.

## Extension — stretch-vertical solicited applications

Added 2026-04-24 after Strala application.

There's a third category alongside SOLICITED and UNSOLICITED: **SOLICITED-STRETCH-VERTICAL**. This is when Jeff applies to a posted role where the vertical fit gap was known and acknowledged before applying (documented by me pre-submission).

Examples:
- **Strala (2026-04-24)**: P&C insurance claims / TPA seller required. Jeff's background is healthcare tech, HCM, AI workflow — different vertical. Gap acknowledged before submission. Submitted anyway because the stage, culture, and sales shape fit (Founders Fund post-Series B, player-coach, multi-million MSA negotiation).

**Signal rule for stretch-vertical applications:**
- Decline or silence is NOT signal about Jeff's profile or application quality
- It IS signal about vertical-specific ATS screening that Jeff cannot overcome without an insider story
- Do not feed these declines into filter tuning, cover letter adjustment, or positioning calibration

**The three categories, unified:**

| Category | Fit gap known upfront? | Decline is signal? |
|----------|------------------------|---------------------|
| SOLICITED, in-vertical | No | YES — read it |
| SOLICITED, stretch-vertical | Yes (documented pre-submission) | NO — ignore |
| UNSOLICITED (no active role) | N/A | NO — ignore |

**Application tracking taxonomy for any future submission log:**
- Tag every submission with one of: `SOLICITED_FIT`, `SOLICITED_STRETCH`, `UNSOLICITED`
- For `SOLICITED_STRETCH`, also tag the specific gap (e.g., "P&C claims vertical gap" for Strala)
- Base-rate math for Jeff's conversion % should ONLY include `SOLICITED_FIT`
- Stretch and unsolicited are "shots on goal" tracked separately, not averaged into the conversion rate
