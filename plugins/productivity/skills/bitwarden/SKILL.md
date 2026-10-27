---
name: bitwarden
description: "Use Bitwarden (open-source password manager, 1Password alternative) for Dean's and client credentials, and Bitwarden's CLI / Secrets Manager to keep API keys out of .env files, chat and git when developing with Claude Code. Use when Dean asks about password management, sharing credentials with a client or teammate, storing API keys or secrets for projects, replacing 1Password or LastPass, or mentions Bitwarden or Vaultwarden."
metadata:
  pricing: freemium
  cost: "Free plan (unlimited passwords and devices); Premium $19.80/yr; Families $47.88/yr; Teams $4/user/mo; Enterprise $6/user/mo (as of 2026-10-27). Secrets Manager has its own plans (check pricing)."
  tags: [passwords, secrets, security, cli, 1password-alternative]
---

# Bitwarden

[Bitwarden](https://bitwarden.com) is an end-to-end encrypted password manager. Its clients and server are open source ([bitwarden/server](https://github.com/bitwarden/server), AGPL plus a Bitwarden License for some features).

## For Dean

- **Cloud, free plan** covers one person: unlimited passwords and devices, plus sharing with one person. **Premium ($19.80/year)** adds the TOTP authenticator, attachments, emergency access and security reports, and is worth it.
- **Client handover:** share credentials through a Bitwarden Organization collection or **Send** (expiring, password-protected), never by email or chat. At the end of a project, transfer ownership and rotate anything you've seen.
- **Self-hosting:** the official server is possible but heavy. The community **Vaultwarden** (Rust, AGPL, unofficial) is lightweight and popular for personal use. Either way, you own backups, updates and HTTPS. Cloud is the safer default unless there's a real data-control need.

## Secrets in development (with Claude Code)

- **Never paste secrets into chat or prompts**, and don't let Claude read vault items. Claude must not run `bw unlock`, `bw get password` or `bws secret get` and print the output.
- Inject secrets into the process instead of writing `.env` files:
  - **Bitwarden Secrets Manager** (`bws`): `bws run -- npm run dev` injects a project's secrets as environment variables. A machine-account access token is stored by Dean, not in the repo.
  - **Password Manager CLI** (`bw`): Dean unlocks it in Dean's own terminal session (`export BW_SESSION=...`), and scripts read what they need without echoing.
- Keep `.env*` in `.gitignore` and commit an `.env.example` with names only. Platform secrets (Vercel, Railway) for deploys; see `security-review` for the rest.

## Don't

- Don't store client secrets in Dean's personal vault without a shared org or collection the client controls.
- Don't use SMS 2FA when TOTP or passkeys are available. Turn on 2FA for the Bitwarden account itself.
