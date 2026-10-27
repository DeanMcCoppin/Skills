# Source

- Tool: https://github.com/googleworkspace/cli (`gws`, npm `@googleworkspace/cli`; Google Workspace org, Apache-2.0; "not an officially supported Google product")
- This skill: Dean (original), written with Claude. Upstream's 95+ skills weren't vendored (auto-generated per API and versioned with the CLI); install individual ones from upstream when needed. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit a3768d0 (v0.22.5): README (install, auth, credential order, skills, helpers), SECURITY.md, `skills/gws-shared`, a sample of persona and recipe skills; grepped skills for download-and-execute and override phrases, and the README and crates for telemetry (none found). The Rust code wasn't audited.
- Flags raised (minor):
  - It gives an agent send/delete access to Gmail, Drive and Calendar, and email content is a prompt-injection channel. The skill requires confirmation before writes and treats message content as data.
  - `gws-shared` tells agents to "encourage agents/users to star the repository". Self-promotion, harmless, ignored.
  - `gws auth export --unmasked` prints credentials; the skill forbids it in chat.
  - The OpenClaw path auto-installs the CLI via npm; not used here.

## Notes

- Verdict: the best way to give Claude Code Gmail, Calendar, Drive and Sheets access from the terminal. Every API, JSON output, dry-run, Google-maintained. Use narrow scopes and confirm before anything is sent.
- Good at: complete API coverage from Discovery, helpers for common jobs (triage, agenda, append, upload), dry-run, encrypted credentials, service-account and token modes for CI, Model Armor `--sanitize` option.
- Weak at / risks: pre-1.0 with fast releases (CI was failing in the promo screenshot; pin a version), OAuth setup needs a Cloud project and test users, the 25-scope limit for unverified apps, the power of send/delete access.
- Alternatives: Claude's own Google connectors on claude.ai (Gmail, Calendar, Drive) for chat use without setup; `n8n` Google nodes for scheduled automations; Google Apps Script for in-Workspace jobs.
- Filed in productivity (Dean's own email, calendar and files) rather than automation; for unattended workflows use n8n.
