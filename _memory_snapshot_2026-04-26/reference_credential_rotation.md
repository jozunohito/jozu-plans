---
name: Credential rotation tracker — incident 2026-04-21
description: Live status of which passwords/tokens are rotated vs pending; iPhone-only rule
type: reference
originSessionId: b76896f1-74c9-4dc1-9c8f-284044f2d492
---
**Ground rule:** All credential work from iPhone only until the Windows PC is wiped and reinstalled.

## Rotated (confirmed)
| Service | Date | Notes |
|---|---|---|
| Microsoft 365 (primary) | 2026-04-21 | Rotated 2x, all sessions revoked, MFA active |
| Outlook (jozuconsultinggroup@outlook.com) | 2026-04-21 | OneNote vault host; sessions revoked |
| GitHub (password) | 2026-04-21 | |
| Yahoo | 2026-04-21 | |
| Cloudflare | 2026-04-21 | 2FA enabled, DNS verified, audit log clean |
| LinkedIn | 2026-04-22 | |
| GoDaddy | 2026-04-22 | |
| GitHub PATs | 2026-04-22 | Tokens page confirmed empty; no PATs existed |
| GitHub SSH keys | 2026-04-22 | Keys page confirmed empty; no keys existed |
| Apple ID | 2026-04-22 | Passphrase rotated, 2FA on, trusted devices reviewed |
| jozuconsultinggroup@gmail.com | 2026-04-22 | Rotated via Yahoo recovery email path |
| jparagon2002@gmail.com | 2026-04-22 | Old Gmail account, rotated; GA4 property G-343BVDJ9KX was tied to this account; access now granted to jozuconsultinggroup@gmail.com as Administrator |

## Forensic checks completed
- M365 mailbox forwarding rules: 2026-04-22 confirmed clean (no unauthorized rules).
- M365 Sent folder: 2026-04-22 confirmed clean (no unauthorized outbound in incident window).

## Rotated (confirmed) — continued
| Airtable | 2026-04-22 | |
| Apollo | 2026-04-22 | |
| Aimfox | 2026-04-22 | |
| Home WiFi router | 2026-04-22 | |

## Windows PC status
- **Wiped and reinstalled: 2026-04-22.** Clean slate.

## Pending (remaining)
- Every other password that was in the OneNote vault. Audit required: list every service whose password sat in OneNote and rotate anything not yet covered.

## Post-wipe / follow-on tasks
- **Windows Defender** verified ON with real-time protection. Never disable. Root cause of the 2026-04-21 incident was Defender being OFF when the .exe ran.
- **Malwarebytes** reinstalled on clean machine.
- **Bitwarden** (or 1Password) set up on clean Windows + iPhone. Paper Apple ID passphrase must go in FIRST before paper is lost.
- **SSH + GPG keys** generated on clean machine, added to GitHub. Enable GitHub vigilant mode after signing keys are in place.
- **IC3 report** at https://www.ic3.gov.
- **Credit freeze** at Equifax, Experian, TransUnion.
- **haveibeenpwned.com** notifications on all active email addresses.
- Consider forensic checks on Outlook.com secondary account.

## Post-wipe migration
- Move vault from OneNote to Bitwarden or 1Password. AFTER PC wipe only.

## External reports
- IC3 report: https://www.ic3.gov
- Credit freeze at Equifax, Experian, TransUnion.
- haveibeenpwned.com notifications on all active email addresses.

## How to apply
Update this file whenever a rotation or forensic check completes. Keep pending list current. When Jeff references a service, cross-check this file before assuming the credential is safe.
