# J4 — Limits Workaround Research
**Agent**: J4 Limits Workaround Research
**Date**: 2026-04-24
**Mission**: Close the fetcher and verification gaps that produced dead-URL waste in the 2026-04-24 sourcing pass. APEX RULE applied — this document only recommends workarounds that actually function. Where something doesn't work, that is stated plainly.

---

## Executive Summary — What Works, What Doesn't

| Gap | Recommended Workaround | Reliability |
|---|---|---|
| 1. JS-rendered ATS pages | Direct ATS public JSON APIs (Greenhouse, Lever, Ashby, Workable, Workday) | High — these are the primary source of truth |
| 2. Federal contractor 403s | USAJobs.gov API (federal) + ClearanceJobs (cleared) + Workday API for contractors on Workday | Mixed — federal-direct works, contractor-direct mostly doesn't |
| 3. LinkedIn auth-gating | Guest endpoints + Jeff-in-tandem live verification | Medium — guest works for discovery; Jeff confirms in real time |
| 4. Aggregator cache lag | Discovery-only role; ALWAYS cross-reference primary ATS before surfacing | High when enforced as SOP |
| 5. Ghost reqs | Multi-signal scoring (age, comp band, named hiring manager, funding date, recent exec hire) | Medium — improves confidence; never deterministic |
| 6. Hidden in-person traps | JD full-text scan + About page + Glassdoor sentiment + conservative default | High when run as a checklist |

---

## Gap 1 — JS-Rendered Career Pages

### Current limitation
WebFetch returns the HTML shell only. Sierra (custom careers), Cato (custom), and most React/Next.js careers pages render content client-side after the page loads. Result: empty job descriptions, missing "primarily in-person" footers, and no apply URLs.

### Recommended workaround — use the ATS public JSON APIs directly
Most JS-rendered career pages are thin wrappers over a public ATS feed. These feeds are the source of truth and require no auth, no headless browser, and no anti-bot evasion.

**Greenhouse** (no auth, not rate-limited)
- List jobs: `GET https://boards-api.greenhouse.io/v1/boards/{board_token}/jobs`
- Single job (full content): `GET https://boards-api.greenhouse.io/v1/boards/{board_token}/jobs/{job_id}?content=true`
- Departments: `GET https://boards-api.greenhouse.io/v1/boards/{board_token}/departments`
- Docs: https://developers.greenhouse.io/job-board.html
- `board_token` is the slug in the company's careers URL (e.g., `boards.greenhouse.io/airbnb` -> token = `airbnb`).

**Lever** (no auth)
- List: `GET https://api.lever.co/v0/postings/{clientname}?mode=json`
- Filter parameters: `team`, `department`, `location`, `commitment`, `level`, `skip`, `limit`
- Docs: https://github.com/lever/postings-api

**Ashby** (no auth, ~100 req/min unofficial limit)
- REST: `GET https://api.ashbyhq.com/posting-api/job-board/{clientname}?includeCompensation=true`
- Always include `includeCompensation=true` to capture comp bands when posted.
- GraphQL fallback: `https://jobs.ashbyhq.com/api/non-user-graphql` (used by the public job board UI itself)
- Docs: https://developers.ashbyhq.com/docs/public-job-posting-api

**Workable** (no auth)
- Account/jobs: `https://apply.workable.com/api/v3/accounts/{subdomain}/jobs` (POST with empty filters body)
- Single job: `https://apply.workable.com/api/v3/accounts/{subdomain}/jobs/{shortcode}`

**Workday** (no auth, used by most large enterprises and many federal contractors)
- List: `POST https://{tenant}.wd{N}.myworkdayjobs.com/wday/cxs/{tenant}/{site}/jobs`
- Body: `{"appliedFacets":{},"limit":20,"offset":0,"searchText":""}`
- Detail: `GET https://{tenant}.wd{N}.myworkdayjobs.com/wday/cxs/{tenant}/{site}/job/{external_path}`
- Tenant + site are visible in the careers URL. List endpoint returns thin records; detail endpoint returns the full JD.

### Honest assessment
- Direct API call: works on ~85% of properly hosted ATS pages. **This is the recommended default.**
- Headless browser (Playwright preferred over Puppeteer in 2026 for cross-browser + auto-waits): only required for fully custom careers pages (Sierra, Cato, some FAANG-internal builds). Cost overhead is real — only invoke when API path fails.
- Browserless.io managed headless infra (~$50-200/mo) is the "license-and-go" option if Jeff wants to remove this gap entirely without standing up local Playwright.

### What doesn't work
- WebFetch on JS-rendered shells. Confirmed yesterday on Sierra and Cato. Stop trying.
- Generic web scrapers without User-Agent + cookie handling on Cloudflare-fronted custom pages.

---

## Gap 2 — Federal Contractor Anti-Bot

### Current limitation
Leidos, SAIC, Booz Allen, MITRE, CACI, Deloitte, PwC return 403 to default User-Agent. Many sit behind Akamai or Cloudflare bot protection that goes well beyond UA sniffing — they fingerprint TLS, headers, hardware concurrency, and WebDriver flags.

### Recommended workaround — multi-source, not bypass
Federal contractor anti-bot is genuinely hard to defeat ethically. The right move is to source the same role data from less-defended channels rather than fight the front door.

**Primary: USAJobs.gov API** (federal-direct only — not contractor)
- Endpoint: `https://data.usajobs.gov/api/Search`
- Free API key required: register at https://developer.usajobs.gov
- Returns currently open federal Job Opportunity Announcements as JSON.
- Use for federal-direct GS-13/14/15 roles, not for contractor-side reqs.

**Primary for cleared roles: ClearanceJobs.com**
- No public API documented. Mirror surface is web-only.
- Workflow: targeted Google site search (`site:clearancejobs.com "VP" "revenue"`) for discovery, then manual click-through.
- Cleer / CleerJobs and IntelligenceCareers.com are similar mirrors with similar access constraints.

**Workday-hosted contractors** (many federal contractors run Workday careers)
- Leidos: `careers.leidos.com` is custom — not Workday. Anti-bot is real.
- Booz Allen: uses iCIMS, not Workday. iCIMS has a public job feed at `https://careers-bah.icims.com/jobs/search?ss=1&searchKeyword=&searchLocation=&in_iframe=1` but anti-bot may still trigger.
- Many smaller defense primes (CACI, ManTech, GDIT divisions) use Workday — try the Workday endpoint pattern first.

**User-Agent for legitimate verification** (last resort, ethical use only — verifying a public posting Jeff intends to apply to)
```
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.9
Accept-Encoding: gzip, deflate, br
```
This will defeat the simplest anti-bot but not Akamai/Cloudflare-protected sites. Don't pretend otherwise.

### Honest assessment
- We **cannot** reliably verify contractor-direct URLs at the same volume we verify Greenhouse/Lever URLs.
- Acceptance: for federal contractor roles, surface to Jeff as "discovered, verification deferred — Jeff to confirm at apply time." Do not pretend the URL is verified.
- Aggregator mirrors (ClearanceJobs, Indeed) are the realistic primary discovery surface for cleared roles.

---

## Gap 3 — LinkedIn Auth-Gating

### Current limitation
LinkedIn shows full job posts only to logged-in users. Default fetchers see the public shell + a "sign in to see more" prompt. Company employee headcount and growth charts are entirely auth-gated.

### Recommended workaround — guest endpoints + Jeff-in-tandem
LinkedIn does serve a real public surface to non-logged-in visitors. Two endpoints work today (2026-04):

- Search: `https://www.linkedin.com/jobs-guest/jobs/api/seeMoreJobPostings/search?keywords={query}&location={location}&start={offset}` — returns parseable HTML cards with job ID, title, company, location, posted-ago.
- Job detail: `https://www.linkedin.com/jobs-guest/jobs/api/jobPosting/{job_id}` — returns the full JD HTML including description, seniority, employment type, function.

### Recommended live workflow (Jeff-in-tandem)
This is the practical play and the one I recommend by default:
1. J1/J2/J5/J7 surface a LinkedIn job URL with the guest-API JD pre-extracted.
2. Agent flags any field that requires auth (employee count, hiring manager profile, mutual connections).
3. Jeff (logged in) opens the URL, confirms still-open + funded signals + grabs the gated fields, reports back yes/no.
4. Surface decision is tracked in the application log.

This is faster and lower-risk than the third-party scraper route.

### Third-party LinkedIn scraping APIs (assess but don't default to)
- **Phantombuster** — ~$59-200/mo, soft TOS gray area, will get session warnings. Useful only if Jeff authorizes paid + accepts risk.
- **Bright Data LinkedIn dataset** — $500+/mo enterprise. Overkill for one role search.
- **Lix-it.com** — $25-99/mo, focused on LinkedIn People/Company search, not jobs.
- **Apify LinkedIn Jobs Scraper** — $10-49/mo per actor run. Lowest friction. Works for jobs specifically.

**Honest assessment**: LinkedIn explicitly prohibits scraping in TOS. The 2022 hiQ v. LinkedIn 9th Circuit ruling allows scraping of public data, but LinkedIn aggressively rate-limits and may suspend accounts. **Default to the guest API + Jeff-in-tandem.** Authorize Apify only if discovery volume becomes the binding constraint.

---

## Gap 4 — Aggregator Cache Lag

### Current limitation
2026-04-24 surfaced multiple dead URLs from BuiltIn (cache ~24-72h), ZipRecruiter (cache ~48h), Glassdoor (cache ~12-48h), Indeed (cache ~6-24h), RemoteRocketship (cache ~12-24h).

### Recommended workaround — discovery-only, primary-cross-reference rule
**Hard rule**: aggregators are for discovery. Primary ATS is the only acceptable surface URL for Jeff.

### Aggregator ranking by cache freshness (best to worst, 2026-04)
1. **LinkedIn** — guest API reflects current state within ~1-6h
2. **Indeed** — ~6-24h, sponsored postings updated hourly
3. **RemoteRocketship** — ~12-24h, niche but well-maintained
4. **Glassdoor** — ~12-48h, often stale
5. **BuiltIn** — ~24-72h, marketing-driven cache, frequently dead links
6. **ZipRecruiter** — ~24-72h, aggressively re-surfaces stale roles
7. **SimplyHired / CareerBuilder / Monster** — multi-day, do not trust

### Workflow
For any aggregator-discovered role:
1. Extract the company name + role title.
2. Identify the primary ATS (Greenhouse / Lever / Ashby / Workable / Workday).
3. Hit the ATS API directly to confirm the role is live in the source of truth.
4. Surface the **ATS URL**, not the aggregator URL, to Jeff.
5. If the role is not on the ATS but is on the aggregator -> mark `aggregator-only, status uncertain` and do not surface as verified.

### API endpoints with timestamp filters
- LinkedIn guest: `f_TPR=r86400` (last 24h), `r604800` (last 7d) on the search URL.
- Indeed: `fromage=1` (last 24h), `fromage=7` parameter.
- Greenhouse: `updated_after` parameter on `/jobs`.
- Lever: postings include `createdAt` epoch, filter client-side.
- Ashby: postings include `publishedDate`, filter client-side.

---

## Gap 5 — Ghost Postings vs Funded Reqs

### Current limitation
Industry data: ~27-30% of 2026 tech postings are ghost (no funded req, evergreen pipeline-builder, or already-filled-but-still-listed).

### Recommended workaround — multi-signal scoring
No single signal is deterministic. Score each role on the funded/ghost axis using these weighted indicators:

**Strong funded signals** (each adds confidence)
- Posted within last 14 days AND not previously seen in pipeline
- Named hiring manager visible (LinkedIn or JD)
- Comp band published with reasonable spread (<40% midpoint-to-ceiling)
- Specific scope (named accounts, specific quota, named tech stack)
- Recent funding announcement (<60 days) — round size + headcount math supports the role
- Recent CFO / VP People / VP Sales hire on LinkedIn (within 90 days)
- LinkedIn shows headcount growth in target function over last 90 days

**Strong ghost signals** (each subtracts confidence)
- "We're always looking for talent" / "Join our talent community" language
- Posting older than 60 days with no description changes
- Same role re-listed every few weeks with fresh date
- No comp band in a state that mandates disclosure (CA, CO, WA, NY, IL)
- Buzzword-heavy JD with no specific scope, deal size, or stack
- Identical req number appears across multiple location postings (often a distributed evergreen)

### Scoring SOP
- 3+ strong funded signals AND <2 ghost signals -> **High confidence funded** (surface to Jeff for fast-lane apply)
- 2 funded AND 2 ghost -> **Medium** (surface with "verify funding before apply" flag)
- 1 funded OR 3+ ghost -> **Low** (do not surface unless company is on Jeff's must-pursue list)

---

## Gap 6 — Hidden In-Person Traps (Sierra Pattern)

### Current limitation
JD says "remote-first" in the headline but late paragraph or bullet says "primarily based in San Francisco" or "expected in office 3 days/week." Yesterday's Sierra surface was the trigger.

### Recommended workaround — full-text checklist scan
Run every JD through this string match before surfacing:

**Disqualifying phrases (auto-flag)**
- `primarily based in`
- `primarily in-person`
- `expected in office`
- `in-office X days`
- `hybrid`
- `must be located in`
- `must reside in` (when paired with a specific city)
- `headquartered in` (when paired with location requirement)
- `relocate` / `relocation`
- `travel up to` (>25% is functionally in-person)

**Cross-checks**
1. Company About page: search for "headquartered" — if they have an HQ and the JD doesn't say "remote-first" twice, default to "in-person likely required."
2. Glassdoor reviews: scan last 90 days for "in-office," "RTO," "return to office" — three or more recent mentions = real RTO pressure.
3. LinkedIn company page: check "Workplace type" tag if present.
4. Recent leadership posts: scan founder/CEO posts for RTO advocacy.

### Conservative default
**Assume some in-person requirement for any company with a stated HQ unless the JD explicitly contains "remote-first" or "fully remote" twice.** This is the cheapest filter and catches Sierra-pattern traps reliably.

### Surface format to Jeff
Add `[REMOTE-VERIFIED]`, `[HYBRID-FLAGGED]`, or `[IN-PERSON-LIKELY]` tag to every role title in the surface log. No role goes to Jeff without this tag.

---

## Verification SOP — All Sourcing Agents (J1, J2, J5, J7) and Live Jeff-Tandem

```
1. Identify primary ATS (Greenhouse/Lever/Ashby/Workable/Workday) -> hit API directly. No HTML scraping unless API fails.
2. Confirm role is live in the ATS API response (not just cached on aggregator).
3. Run full-JD text scan for the 11 in-person trap phrases (Gap 6 list).
4. Score role on the funded vs ghost rubric (Gap 5) — minimum 2 funded signals or do not surface.
5. Capture: posted date, comp band, hiring manager (if visible), apply URL from ATS.
6. Cross-check company funding date and recent exec hires (60-90 day window).
7. For LinkedIn-discovered roles, hit guest API for full JD; flag any auth-gated field for Jeff to verify live.
8. For federal contractor roles, mark `verification-deferred-to-Jeff` — do not pretend URL is verified.
9. Surface to Jeff: ATS URL (not aggregator URL) + remote tag + funding score + ghost-risk flag.
10. Log every surface in applications_log.md with verification status; track dead-URL rate weekly.
```

---

## Priority Workarounds for Jeff to Authorize

Ranked by impact-to-cost ratio:

1. **USAJobs.gov API key** — free, 5-minute registration, immediately unlocks federal-direct verification. **Authorize today.**
2. **Local Playwright install** — free, ~30 min setup. Unlocks the ~15% of fully custom JS-rendered careers pages (Sierra, Cato, others). **Authorize today.**
3. **Apify LinkedIn Jobs actor** — $10-49/mo per run. Authorize only if guest-API + Jeff-tandem hits volume ceiling. **Defer until needed.**
4. **Browserless.io managed headless** — $50-200/mo. Skip if local Playwright is set up. **Defer.**
5. **Bright Data / Phantombuster** — $200-500+/mo. Not recommended unless scale forces it. **Defer.**

Total recommended initial authorization: $0 (USAJobs API + local Playwright are both free).

---

## Sources

- [Greenhouse Job Board API](https://developers.greenhouse.io/job-board.html)
- [Lever Postings API](https://github.com/lever/postings-api)
- [Ashby Public Job Posting API](https://developers.ashbyhq.com/docs/public-job-posting-api)
- [USAJobs Developer API](https://developer.usajobs.gov/api-reference/get-api-search)
- [LinkedIn Guest Jobs API documentation (community)](https://dev.to/agenthustler/how-to-scrape-linkedin-job-listings-in-2026-public-data-without-login-5094)
- [Workday Careers JSON Pattern](https://jobo.world/ats/workday)
- [Playwright vs Puppeteer 2026](https://www.browserstack.com/guide/playwright-vs-puppeteer)
- [Ghost Job Detection Signals 2026](https://hidejobs.com/learn/ghost-jobs)
- [Ghost Jobs Congressional Research Service](https://www.congress.gov/crs-product/IF12977)
- [403 Web Scraping Mitigation](https://scrapfly.io/blog/posts/403-forbidden-web-scraping)
