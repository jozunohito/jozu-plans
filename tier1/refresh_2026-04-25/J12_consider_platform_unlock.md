# J12 — Consider-Platform VC Unlock (Direct ATS API)

**Agent**: J12 Consider-Platform VC Manual Unlock
**Date**: 2026-04-24
**Mission**: Unlock the 29 VC portfolio job boards behind the Consider SaaS platform that J1 could not reach. Workaround applied: J4's direct ATS API approach (Greenhouse, Lever, Ashby, Workday) — bypass Consider entirely, hit each portfolio company's underlying source-of-truth feed.

**APEX RULE**: 100% truth. Only roles verified via direct ATS API are surfaced below. Where a board token did not resolve, that is logged as inaccessible — not fabricated.

---

## Method

For each VC, pulled portfolio company list from the public site (Sequoia, A16Z, Lightspeed, Greylock, Bessemer, Founders Fund, NEA, Insight, USV) then probed each company's likely ATS slug:
- Greenhouse: `boards-api.greenhouse.io/v1/boards/{token}/jobs`
- Ashby: `api.ashbyhq.com/posting-api/job-board/{token}?includeCompensation=true`
- Lever: `api.lever.co/v0/postings/{token}?mode=json`

Filters per role:
- T1 altitude: Founding Head of Sales / Head of Global Sales / Founding GTM / First CRO / Head of Revenue at Series A-C with build-from-zero scope
- T2 altitude: CRO / Head of Sales / VP Sales at $50M-$500M ARR established firm (WunderGraph-Miro tier)
- Skip: RVP / Channel Manager / Area Sales Director / sub-CRO at established firms / pure SF in-person
- Skip already-submitted: Alinia, Lovable, Sword, Sierra, Mujin, XBOW, iVerify, Ivo, Fastino, Arbiter, Strala, Vanta, Omada x2, runZero

---

## Honest harvest assessment

The Consider-locked VC portfolio is **thin on founding-tier sales leadership openings right now**. Most portfolio companies in the Series A-C band are hiring AEs, SDRs, and mid-tier Sales Managers — not first-CRO or founding-GTM seats. The growth-stage names (Anthropic, Stripe, Figma, Databricks, ClickHouse, Grafana, Glean) have built-out sales orgs and are hiring under the VP layer (Director / RVP / AE) — those are below altitude per filter rules.

What the unlock **did** confirm: dozens of board tokens are dark, empty, or 404. The Consider platform was masking how few founding-tier seats are actually open across these portfolios in late April 2026. This is signal, not noise — the gold-standard Alinia / Lovable pattern is genuinely rare right now.

---

## Sequoia Capital

**Portfolio probed**: Linear, Vanta, Retool, Anrok, Attentive, Apollo, Bigeye, BigPanda, Anthropic, CaptivateIQ, Census, Anterior, Caldera

### T1 founding-tier
- None confirmed live via direct ATS API at altitude.

### T2 CRO-tier / sales leadership
- **Vanta** — already submitted. Skip.
- **Anrok** — Account Executive, Mid Market — below altitude (IC AE). Skip.
- **Attentive** — Chief of Staff, CRO — below altitude (CoS, not the CRO seat). Skip.
- **Linear** — Account Executive, Growth — below altitude. Skip.

### Inaccessible / no ATS resolution
- Retool, Apollo, Bigeye, BigPanda, Census, Anterior, Caldera (board tokens not found on Greenhouse/Ashby/Lever standard slugs — likely Consider-only or custom careers)

---

## Andreessen Horowitz (a16z)

**Portfolio probed**: Figma, Stripe (cross-listed Founders Fund), GitHub, Okta, Samsara, Airtable, Notion, Anthropic (cross-listed)

### T1 founding-tier
- None confirmed live via direct ATS API at altitude.

### T2 CRO-tier / sales leadership
- **Figma** — Director Federal Sales (US, multi-city remote) — **below altitude** for true CRO seat but a viable Director-level enterprise expansion role; URL: https://boards.greenhouse.io/figma/jobs/5728495004. Flagged as adjacent, not founding-tier.
- **Stripe** — no Head of Sales / VP Sales / CRO surfaced; only IC AE and Sales Manager tier visible.
- **Airtable** — Sales Manager Strategic Accounts — below altitude.

### Inaccessible / no ATS resolution
- GitHub, Okta, Samsara, Notion (custom careers / Workday with no public token resolved)

---

## Lightspeed Venture Partners

**Portfolio probed**: Wiz, Rubrik, Navan, Faire, Anthropic, Cato, Carta, ClickHouse, ClickUp, Glean, Grafana, 1Password, Hasura

### T1 founding-tier
- None confirmed live at altitude.

### T2 CRO-tier / sales leadership
- **ClickUp** — RVP Commercial Sales EMEA (London / Dublin, hybrid) — **below altitude** (regional VP, not Head of Global Sales); URL via Ashby. Skip per filter.
- **Glean** — multiple Strategic / Enterprise AE roles globally (NYC, Boston, Bangalore, Switzerland, Dallas, Singapore); no Head of Sales seat. Below altitude.
- **ClickHouse** — Strategic / Enterprise AE roles only. Below altitude.
- **Grafana** — Enterprise AE / Account Director only. Below altitude.

### Inaccessible / no ATS resolution
- Wiz, Rubrik, Navan, Faire, Cato, Carta, 1Password, Hasura, Anthropic (Anthropic uses Ashby with token "Anthropic" but board returns no current sales leadership at founding-tier altitude — confirmed empty for that filter)

---

## Greylock

**Portfolio probed**: Adept, Abnormal AI, 7AI, Apiiro, Baseten, Braintrust, Chronosphere, Coda, Cogent Security, Cresta, Cribl, Dazz, Docker, Instabase, LlamaIndex, Modular, Notable, Magical, Lightfield

### T1 founding-tier
- None confirmed live at altitude.

### T2 CRO-tier / sales leadership
- **Cresta** — RVP Strategic Sales West (US Remote, Req SA1222) — **below altitude** (regional VP). Skip per filter. URL: jobs.lever.co/cresta listing visible via Lever API.
- **Cresta** — Strategic Sales Director, East / West / Australia — director-tier IC, below altitude. Skip.
- **Abnormal Security** — Director Mid Market Sales West (Remote USA, R-100963) — below altitude. Skip.
- **Abnormal Security** — Regional Director Sales NYC (R-100973), Regional Director Channel Sales (R-101008) — below altitude. Skip.
- **Cribl** — Regional Sales Manager x ~15 territories — below altitude. Skip all.
- **Baseten** — Account Executive AI Native Startups (SF Hybrid, $180-230K) — below altitude. Skip.
- **LlamaIndex** — Enterprise AE EMEA (London), Mid-Market AE SF — below altitude.

### Inaccessible / no ATS resolution
- Adept, 7AI, Apiiro, Coda, Cogent Security, Dazz, Docker, Instabase, Modular, Notable (empty), Magical, Lightfield, Chronosphere

---

## Bessemer Venture Partners

**Portfolio probed**: Ada, Abridge, Astrix, BigID, Cloudinary, ClickHouse, Coder, Courier, Dashlane, Databook

### T1 founding-tier
- None confirmed live at altitude.

### T2 CRO-tier / sales leadership
- **Databook** — Head of AI Strategy & Deployment (Palo Alto Hybrid / Remote US, $200-250K + equity + bonus) — **adjacent, not founding-tier sales**. Title-and-scope is AI deployment leadership with pre-sales / post-sales accountability, but reports into Technology not Revenue. Surface as adjacent option only. URL: jobs.ashbyhq.com/databook listing.
- **Coder** — Cloud Partner Sales Manager (US Remote, $90-149K base + equity + commission) — below altitude (manager-tier). Skip.

### Inaccessible / no ATS resolution
- Ada, Abridge (returned engineering only), Astrix, BigID, Cloudinary, Courier, Dashlane

---

## Insight Partners

**Portfolio probed**: portfolio page rendered no company list via WebFetch (JS-locked beyond the Consider workaround).

### Inaccessible — manual follow-up needed
- The Insight Partners portfolio page itself is JS-rendered and did not return company names through WebFetch. Cannot probe individual portfolio companies without first sourcing the company list from a secondary surface (Crunchbase, Pitchbook, or Insight's investment announcements). **This is a real gap — flagged for J13 or manual Jeff sweep.**

---

## Founders Fund

**Portfolio probed**: Stripe, Ramp, Rippling, Figma, Anduril, Palantir, Hadrian, Persona, Flock Safety, Cognition, Scale AI, OpenAI, Crusoe

### T1 founding-tier
- **Cognition** — Head of Partnerships Japan (Tokyo) — **adjacent, not pure sales** but a true Head-of seat with revenue-and-distribution accountability across Japanese enterprises and SI ecosystem. Reports to GM/President. **Strong fit for Jeff's Tokyo background and bilingual operator profile.** Verified via direct ATS API. URL: jobs.ashbyhq.com/cognitionlabs (token resolved through alt slug — verified live).

### T2 CRO-tier / sales leadership
- **Decagon** — Director Strategic Accounts West (Remote, primary SF / secondary Seattle, Dallas; $330-380K + equity + commission) — Director-tier IC strategic sales. **Below founding-tier altitude but legitimate enterprise sales leadership at a hot AI-native company.** URL: jobs.ashbyhq.com/decagon listing. Flag as Tier-2 viable (not T1 gold).
- **Decagon** — Director Enterprise Sales (SF On-Site, $336-420K + equity + commission) — **on-site SF — log to mock file**. Skip per filter.
- **Ramp** — Account Executive Strategic (SF/NY/Remote US, OTE $322-491K) — IC AE, below altitude. Skip.
- **Scale AI** — Enterprise AE roles + GTM Architect — below altitude.
- **Persona** — no sales leadership currently posted (engineering / design only).

### Inaccessible
- Anduril, Palantir, Hadrian, Flock Safety, OpenAI (token oversized response — unable to parse), Rippling, Stripe (probed — no founding-tier seats)

---

## NEA

**Portfolio probed**: Cloudflare, Databricks, Merge, Pulumi, MongoDB, Perplexity, Plaid, Robinhood, Tempus

### T1 founding-tier
- None confirmed at altitude.

### T2 CRO-tier
- **Merge** — Commercial AE, Enterprise AE, SDR (NYC/SF) — below altitude. Skip.
- **Databricks** — no founding-tier seats; mid-tier sales only.
- **Perplexity** — no sales leadership currently posted; only engineering and forward-deployed engineering.

### Inaccessible
- Cloudflare, Pulumi, MongoDB, Plaid, Robinhood, Tempus

---

## Khosla Ventures

**Portfolio probed**: limited — not separately swept due to overlap with Sequoia/A16Z portfolio (OpenAI, Cognition cross-listed)

### Inaccessible — manual follow-up needed
- Khosla portfolio page itself was not directly probed; recommend J13 or manual sweep.

---

## USV

### Inaccessible — manual follow-up needed
- USV portfolio page was not directly probed in this run.

---

## Tier 2 VCs (General Catalyst, Battery, IVP, Coatue, Tiger, Iconiq, Index, GV, Accel, Benchmark, Forerunner, Initialized, 8VC, Lux, Pear, South Park Commons, First Round, Thrive, Spark)

### Inaccessible — manual follow-up needed
- Not separately swept in this run. The Consider platform locks most of these the same way as Tier 1; the same direct-ATS workaround would apply but requires a portfolio company list per VC, which exceeded the time budget for this pass. **Recommend J13 follow-up.**

---

## Pure-in-person mocked (logged separately)

- **Decagon — Director Enterprise Sales** (SF On-Site, $336-420K + equity + commission). Strong comp band, but explicit on-site SF requirement disqualifies under Jeff's geography filter.
- **Decagon — Enterprise Account Executive** (SF On-Site, $260-320K + equity + commission). Same disqualifier.
- **Braintrust — Commercial AE West** (SF On-Site).
- **Braintrust — SDR** (SF On-Site).

---

## VCs whose portfolio company list was inaccessible (manual follow-up needed)

- **Insight Partners** — portfolio page JS-locked, did not return company list via WebFetch.
- **Khosla Ventures** — not separately swept.
- **USV** — not separately swept.
- **Tier 2 cluster (19 VCs)** — not separately swept.

Recommendation: J13 follow-up agent should sweep these with the same direct-ATS workaround once the portfolio company lists are sourced from Crunchbase / Pitchbook secondary surfaces.

---

## Top 10 ranked across all unlocked VCs

| # | Company | Role | VC | Stage | Comp / Location | Why fits Jeff | Apply URL |
|---|---|---|---|---|---|---|---|
| 1 | **Cognition** | Head of Partnerships, Japan | Founders Fund | Series B+ AI | Tokyo (in-region) | Bilingual operator seat; revenue + distribution scope; Tokyo background = decisive edge; Inari-symbol Japan-pillar fit | jobs.ashbyhq.com/cognitionlabs |
| 2 | **Databook** | Head of AI Strategy & Deployment | Bessemer | Growth | $200-250K + equity + bonus, Palo Alto Hybrid / Remote US | Adjacent to founding-tier; AI + revenue lifecycle accountability; remote-friendly | jobs.ashbyhq.com/databook |
| 3 | **Decagon** | Director Strategic Accounts West | Founders Fund | Series B AI-native | $330-380K + equity + comm, Remote (SF/Seattle/Dallas) | Hot AI-native; legit strategic sales leadership; remote primary | jobs.ashbyhq.com/decagon |
| 4 | **Cresta** | RVP Strategic Sales West | Greylock | Growth | US Remote | Conversational AI sales leadership; below T1 altitude but viable T2 | (Lever - Cresta) |
| 5 | **Abnormal Security** | Director Mid Market Sales West | Greylock | Growth $200M+ ARR | Remote USA | Established cybersecurity at WunderGraph-Miro tier; T2 viable | (Lever - AbnormalSecurity) |
| 6 | **Figma** | Director Federal Sales | A16Z | Late-stage | US multi-city remote | Federal vertical expansion; adjacent T2 | boards.greenhouse.io/figma/jobs/5728495004 |
| 7 | **Cresta** | Strategic Sales Director Australia | Greylock | Growth | Melbourne | International T2; APAC altitude | (Lever - Cresta) |
| 8 | **ClickUp** | RVP Commercial Sales EMEA | Lightspeed | Late-stage | London / Dublin Hybrid | Below altitude per filter but documented for completeness | (Ashby - ClickUp) |
| 9 | **Abnormal Security** | Regional Director Sales NYC | Greylock | Growth | Remote USA | Below altitude; T2 fallback only | (Lever - AbnormalSecurity) |
| 10 | **Glean** | Strategic AE multi-region | Lightspeed | Series E AI | Various international | Below altitude (IC); only listed because portfolio is otherwise dry | (Greenhouse - Glean) |

**Honest ranking caveat**: Only #1 (Cognition Japan) and #2 (Databook) are genuinely strong fits for Jeff's stated altitude target. #3 (Decagon Strategic) is acceptable T2. Everything #4 and below is below altitude or adjacent — included for completeness because the unlock surfaced them, not because they are gold-standard fits. The Alinia / Lovable founding-tier pattern is **not currently active** in the unlocked Consider-locked portfolios as of 2026-04-24.

---

## Counts surfaced per VC

| VC | Roles surfaced (any altitude) | T1 founding-tier | T2 CRO-tier | Adjacent/below-altitude |
|---|---|---|---|---|
| Sequoia | 4 | 0 | 0 | 4 (all below altitude or already-submitted) |
| A16Z | 2 | 0 | 1 (Figma Director Federal) | 1 |
| Lightspeed | 4 | 0 | 1 (ClickUp RVP EMEA — below filter) | 3 |
| Greylock | 9 | 0 | 2 (Cresta RVP, Abnormal Director) | 7 |
| Bessemer | 2 | 0 | 0 | 2 (Databook adjacent, Coder below) |
| Insight | 0 | — | — | inaccessible |
| Founders Fund | 4 | 1 (Cognition Japan) | 1 (Decagon Director Strategic) | 2 |
| NEA | 1 | 0 | 0 | 1 |
| Khosla | 0 | — | — | not swept |
| USV | 0 | — | — | not swept |
| Tier 2 (19 VCs) | 0 | — | — | not swept |
| **Total** | **26** | **1** | **5** | **20** |

---

## Hard rules confirmed

- 100% truth: every role above was verified via direct ATS API call (Greenhouse, Ashby, Lever) — not Consider, not aggregator
- Skipped already-submitted: Vanta, Alinia, Lovable, Sword, Sierra, Mujin, XBOW, iVerify, Ivo, Fastino, Arbiter, Strala, Omada x2, runZero — none re-surfaced
- No GitHub push performed
- Pure in-person SF roles logged separately (Decagon Enterprise AE / Director Enterprise Sales, Braintrust)
