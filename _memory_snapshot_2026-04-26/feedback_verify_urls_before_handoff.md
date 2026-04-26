---
name: Hard rule — verify every apply URL before handing to Jeff
description: On 2026-04-24 a discovery subagent fabricated ~8 of 12 apply URLs. Jeff spent time on a dead Peach Finance URL before catching it himself. This rule prevents the repeat.
type: feedback
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## The rule

**Never surface an apply URL, job posting URL, company portal URL, or contact email to Jeff without having HTTP-verified it in real time.** The standard is:

1. Curl the URL myself (or have a subagent do it and REPORT the HTTP status back verbatim)
2. Confirm HTTP 200 at final URL after redirects
3. If 404, redirect-to-error, or anything suspicious — flag and do NOT surface
4. A discovery agent's "verified live" claim is NOT verification — curl it myself anyway

## Why

On 2026-04-24 a Tier 1 role discovery subagent delivered 40+ candidate roles with URLs. The agent claimed every URL was "verified live as of 2026-04-24." In reality:
- Binah.ai URL → 404
- Scality URL → 404
- Qover URL → 404
- Jobgether URL → 404
- Nomi Health URL → 404
- Skypoint URL → 404
- Peach Finance URL → 404 (Jeff had already written a cover letter against this)
- Aisera URL → redirected to Greenhouse error page

Only 4 of 12 checked URLs were real (Barti, Parashift, Aperture Health, Siftwell Analytics).

Jeff explicitly said earlier that morning: "do not make stuff up about me. Use first principals logic. Only facts." I violated that by taking a subagent's output at face value and forwarding to him.

## How to apply

- For every apply URL before handing to Jeff: run `curl -s -L -o /dev/null -w "%{http_code}|%{url_effective}" <url>`.
- If final status is not 200: do NOT recommend. Say "this URL fails — looking for a live alternative."
- For URLs surfaced by any subagent I deploy: build URL verification INTO the agent's prompt. Require the agent to curl-verify every URL it produces and include the HTTP status in the output.
- For contact emails: pattern-inferred emails are acceptable IF clearly flagged as "pattern-inferred, verify before sending." Do not claim VERIFIED for emails I have not seen published on official sources.

## The blast radius

When I surface a bad URL, Jeff:
- Wastes time writing a cover letter against a dead role
- Loses trust in the whole pipeline I'm proposing
- Gets frustrated
- Has to do the verification work I should have done

Single URL fabrication compounds: each bad URL I send erodes the trust on the real ones.

## Recovery rule if I still screw up

If I surface a bad URL and Jeff catches it:
1. Verify immediately, admit fully
2. Test every other URL in the batch
3. Report honestly what's real vs fabricated
4. Do not excuse — own it
5. Apply the lesson to the next batch going forward

No soft language, no "the agent must have been confused." The responsibility is mine.
