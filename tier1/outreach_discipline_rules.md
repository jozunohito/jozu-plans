# Outreach Discipline Rules — Brand-Protective Operating Doctrine

**Locked:** 2026-04-26 ~05:00 UTC
**Source:** Jeff's brand-risk question 2026-04-25 evening, before bed
**Purpose:** Prevent the en-masse-outreach pattern from triggering brand damage at VCs, recruiters, and inside dense subnetworks. Also prevent LinkedIn algorithmic flagging.

---

## The five caps

### Cap 1 — Weekly applications: **5-7 high-conviction**

Current pace is 3-5/week. Stay there. Do NOT push past 7 in any rolling seven-day window unless the master consolidated list shows a rare cluster of equally-high-fit roles all closing the same week.

### Cap 2 — Weekly Aimfox connection requests: **≤25 total**

Math: 5-7 applications × ~3 leader targets per application = ~15-21 connection requests per week from the apply-to-companies queue.

**M5 founder cold-DM list shares this cap.** The 50-name founder list and the Aimfox queue both fire connection requests through Jeff's LinkedIn account. They are NOT separate budgets.

Allocation default: 18-21 to Aimfox queue (apply-to-companies), 4-7 to M5 cold-DM founders. RGI tags by source (`applied_to` vs `cold_dm_founder`) so the queue can pace correctly.

If a week's apply-to-company volume runs hot (5+ apps, all 3-target), the cold-DM founders defer to the next week. The apply-queue takes priority because each row is tied to an active application.

### Cap 3 — Weekly recruiter DMs: **≤2**

The N6 recruiter list is small (Amy Volas, Daversa, Pierce, Wendt, Roberge — 5 names, plus future additions). They talk to each other inside the CRO/founding-sales recruiter niche.

Default cadence: 1-2 recruiter DMs per week, spaced Tuesday → Thursday morning. Never more than 2 in any rolling seven-day window. Never two on the same day.

### Cap 4 — Same-VC-portfolio applications per rolling 14-day window: **≤2**

VC talent partners (a16z Talent, Sequoia, Greylock, Founders Fund, AI Fund, ICONIQ, Insight) maintain candidate-flow visibility across their portfolio. Three or more applications inside one VC's portfolio in two weeks reads as wide-spray pattern.

Allowed: 2 applications inside one VC's portfolio per 14-day window. Then deferral. Track a per-VC counter in the consolidated master list.

Special handling for AI Fund — Vindexa is already in flight. No additional AI Fund portfolio applications until 2026-05-09 at earliest.

### Cap 5 — Same-vertical-cluster recruiter overlap: **enforce 7-day spacing**

When a recruiter is already in flight (DM sent, awaiting response), do NOT also apply directly to roles that recruiter is known to source for, in the same 7-day window. The recruiter sees the application come through their ATS feed and reads it as bypass.

Worked example: Amy Volas sources for SaaStr-aligned founding-sales seats. If Amy DM is in flight Tuesday, do NOT direct-apply to a SaaStr-aligned founding-sales role on Wednesday. Wait the week.

---

## Stagger discipline

### Same VC's portfolio
- Maximum 2 applications per 14-day window inside one VC's portfolio (Cap 4).
- Track in the master consolidated list with a "VC fund" column. Pre-flight check before every application: how many in this fund's portfolio in the last 14 days?

### Same vertical
- Healthcare-payer cluster, cyber cluster, AI-enterprise cluster — apply across clusters in the same week, not 4-5 deep into one cluster. The diversity itself is the brand-protection signal (Jeff is conviction-applying, not spraying).

### Same week
- Do NOT batch 5 applications on Sunday night. Spread across Mon-Wed-Fri or similar. Brand-risk view: a VC partner who sees 5 portfolio-CEO connection requests with similar plan-tease notes all on Tuesday morning will pattern-match. Spread.

---

## Connection-note hygiene

The locked Aimfox voice template ("Hello [Name], I have submitted to the [Role] role on your website and have built a 90-day plan...") is identical except for first name + role title. Two CEOs in the same dense subnetwork who compare notes WILL notice. Mitigations:

1. **Cluster control over template variation.** The locked template stays as written. Variation is achieved by NOT clustering same-VC same-vertical applications in the same week.
2. **Skip the connection request when the target is a 1st-degree connection** — different motion entirely (DM, not connect with note).
3. **Skip the connection request when Jeff has already DM'd the target in the last 90 days** — the queue dedup rule handles this.

---

## ATS confidentiality reality check

| Detector type | Visibility | Risk level |
|---|---|---|
| Random unrelated company hiring managers | Cannot see Jeff's other applications | None |
| ATS-shared parent / sister-co companies | Same Greenhouse/Lever instance = full visibility | Low (rare config) |
| VC centralized talent platforms (a16z, Sequoia, Greylock, Founders Fund, AI Fund, etc.) | See candidate flow across portfolio | **HIGH within portfolio — Cap 4 is the mitigation** |
| LinkedIn Recruiter customers | Can see Jeff's "Open to Work" + applied-jobs history at the Recruiter tier | **MEDIUM — confirm Open to Work setting** |
| Specialized exec-search firms (Daversa, Pierce, Wendt, Volas, Roberge) | Talk inside the niche | **MEDIUM — Cap 3 is the mitigation** |
| LinkedIn algorithmic flagging on connection-request volume | ~100/week safe on Premium with Aimfox spacing | **LOW at Cap 2 levels** |

---

## Open question Jeff needs to confirm

**LinkedIn "Open to Work" setting.** Two options:
- **Visible to recruiters only** (private flag — only LinkedIn Recruiter customers see)
- **Public to everyone** (green frame on profile photo + visible "Open to Work" banner)

For Jeff's role-search at altitude, recruiter-only is almost always the right setting. Public Open-to-Work signals "actively hunting" to current employer / network in a way that can read as desperation at C-level. Confirm in jozu-status morning.

---

## Per-application pre-flight checklist (apply this every time before submission)

Before clicking apply on any role:

1. ☐ JD experience floor is 10+ years (or unspecified). If single-digit-years, SKIP.
2. ☐ Vertical fit 70+ score on the rubric.
3. ☐ Same-VC-portfolio counter for this fund's portfolio is < 2 in the last 14 days.
4. ☐ Application count in current rolling 7-day window is < 7.
5. ☐ Aimfox queue + cold-DM cap projection for this week stays at ≤25.
6. ☐ No active recruiter in flight on a same-vertical role in the last 7 days.
7. ☐ Resume variant matches role type (VP tri for founding-tier without Fractional CRO; CRO master for established CRO seats with Fractional CRO line).
8. ☐ Cover letter follows voice rules — no em dashes, no choogy, no personal earnings.
9. ☐ Application logged to applications_log.md in the same turn.
10. ☐ Aimfox queue rows generated (or VERIFY-flagged) in the same turn.

If any line fails: STOP and either fix or skip the role.

---

## What this discipline costs Jeff

Two real costs:
1. **Pace constraint** — 5-7 applications per week is slower than a "spray 30 a week" approach. Trade-off: brand integrity over volume.
2. **Decision overhead** — every application now passes a 10-line checklist. Trade-off: prevents StackOne-style auto-rejects and same-VC clustering.

What it buys:
1. **Lower auto-reject rate** at experience-band ATS gates.
2. **Higher accept rate** on Aimfox connection requests (less template-fatigue inside dense subnetworks).
3. **Brand integrity at the recruiter / VC-talent level** — no "Jeff is spraying" signal in the niche.
4. **Scalable for 8-12 week role-search horizon** — no LinkedIn / ATS detection trip-wires.

---

## Source

Jeff Aragon's brand-risk question 2026-04-25 evening: "Are we creating noise and ruining my 'brand' by being so aggressive in our outreach? Can any hiring team figure out that I am going at this en masse, and is that a risk?"

Honest assessment: yes there IS risk, and it concentrates in (a) VC portfolio cross-visibility, (b) specialized recruiter networks, and (c) connection-note uniformity inside dense subnetworks. The five caps + stagger discipline + per-application pre-flight checklist together are the mitigation.

Lock the doctrine. Apply on every application going forward.
