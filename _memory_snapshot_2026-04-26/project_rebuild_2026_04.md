---
name: Malware incident 2026-04-21 and rebuild
description: Full incident detail, compromised scope (OneNote vault), completed and pending remediation
type: project
originSessionId: b76896f1-74c9-4dc1-9c8f-284044f2d492
---
## The attack (2026-04-21)
- Fake recruiter "Kumar" claiming to be CEO of Procurity.AI sent a fake Zoom link.
- Link launched a Windows .exe installer. Ran 6 times.
- Microsoft Defender was OFF at the time.
- Malwarebytes later flagged 6 files as **Trojan.ScreenConnect.abused**. Confirmed Remote Access Trojan.
- Attacker had potential live remote access to the PC.

## Critical compromise
- Password vault lived in **OneNote**.
- OneNote was opened on the infected PC during the window.
- **Assume attacker exfiltrated the entire vault.** Every password in it must be rotated.
- iPhone is clean (Apple sandbox blocked the .exe).
- Windows PC is compromised, offline, awaiting full wipe.

## Rotations completed (from iPhone)
- Microsoft 365 (jeff@jozuconsultinggroup.com): rotated 2x, sessions revoked, MFA holding.
- jozuconsultinggroup@outlook.com (OneNote host): rotated, sessions revoked.
- GitHub: password rotated. **Tokens and SSH keys NOT yet revoked.**
- Yahoo: rotated.
- Cloudflare: rotated, 2FA enabled, audit log reviewed, DNS verified unchanged.
- Bank: notified, handling account.
- LinkedIn: rotated 2026-04-22.
- GoDaddy: rotated 2026-04-22.

## Confirmed non-events
- Utah "unsuccessful" login at 11:39 was Jeff via iCloud Private Relay (AMC PROD app). Not the attacker.
- No confirmed attacker login to any account yet.

## Pending actions (ordered)
1. **Full Windows reinstall.** PC cannot be trusted.
2. **GitHub: delete ALL personal access tokens** (https://github.com/settings/tokens) **and ALL SSH keys** (https://github.com/settings/keys). Password rotation does NOT revoke these.
3. **M365 check:** Sent folder for unauthorized outbound messages, and mailbox forwarding rules (standard exfil persistence).
4. **Remaining vault rotations:** Airtable, Apollo, Aimfox, Apple ID.
5. **Home WiFi router password** (common password, likely in vault).
6. **Every other password that was in the OneNote vault.** Treat entire vault as compromised.
7. **Migrate off OneNote for passwords.** Move to Bitwarden or 1Password AFTER PC wipe.
8. **File IC3 report** at https://www.ic3.gov.
9. **Credit freeze** at all three bureaus: Equifax, Experian, TransUnion.
10. **Subscribe to haveibeenpwned.com notifications** on all active email addresses.

## Ground rules during incident work
- All credential work from iPhone only. No exceptions.
- Assume every password in OneNote is in attacker hands until rotated.
- Do NOT re-enter anything on the PC until fully wiped and reinstalled.
- Keep responses 1-2 lines per step during incident work.

## How to apply
When Jeff mentions any service, check: was its password in the OneNote vault? If unknown, assume yes and flag for rotation. If not yet rotated, surface it in the pending queue. Do not let remediation items drop just because a newer topic came up.
