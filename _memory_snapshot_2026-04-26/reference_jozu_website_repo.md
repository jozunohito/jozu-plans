---
name: Jozu website repo and push workflow
description: Local clone path, GitHub remote, SSH auth setup, and publish workflow for jozuconsultinggroup.com
type: reference
originSessionId: 939cd6e3-3da9-4ed2-9096-649430f0fcd0
---
## Repo

- Local clone: `C:\Users\Jeff\claude-projects\jozu-website\`
- GitHub remote: `git@github.com:jozunohito/jozu-website.git` (SSH)
- Live site: https://jozuconsultinggroup.com via GitHub Pages (CNAME file in repo root)
- Account: jozunohito

## Auth setup (established 2026-04-22 post-wipe)

- SSH key: RSA-4096 at `C:\Users\Jeff\.ssh\id_rsa` (+ `.pub`), no passphrase
- Fingerprint: `SHA256:SBnpxfH+8FWOHkJjKjsjdGZEC+NP5oZOUdXZUbE8Pr8`
- Windows ssh-agent service: `StartupType Automatic`, key loaded via `ssh-add`
- Git config:
  - `user.email = jeff@jozuconsultinggroup.com`
  - `user.name = Jeff Aragon`
  - `core.sshCommand = C:/Windows/System32/OpenSSH/ssh.exe` (routes Git Bash / Claude Bash through the Windows agent so both can push)
- Test command that should succeed: `ssh -T git@github.com` returns `Hi jozunohito! You've successfully authenticated...`

## Publish workflow

1. Edit HTML / CSS / assets in the local clone.
2. `git add` + `git commit` with a descriptive message.
3. `git push` — GitHub Pages rebuilds within ~1 min.
4. Verify live at jozuconsultinggroup.com.

## Notes

- Use Bash tool with the working dir set into `jozu-website/` for git commands, or pass `-C` to git.
- Top-level content files as of setup: index.html, about.html, contact.html, founders.html, plus pillar pages (japan-market-entry, healthcare-payer, enterprise-sales-system, revenue-architecture, etc.) and `case-studies/`, `insights/`, `services/`, `logos/` subdirectories.
- Jeff plans to publish more content regularly starting late April 2026.
