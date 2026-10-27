# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/security-review (+ cloud-infrastructure-security.md) (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: removed the Solana/blockchain section (off-topic, and its `verify` import from @solana/web3.js does not exist); replaced the Express rate limiter with a serverless-safe Upstash example for Next.js; cloud reference: pinned the trufflehog action (was @main), removed a broken `"install": "npm ci"` package.json example (it would recurse), softened "env vars are wrong" to fit Vercel-style hosting; kept the warning comment about `$N` placeholders (skill arguments substitute them).

## Notes

- Verdict: solid default checklist for any feature touching auth, input, secrets or payments; run it before deploys.
- Good at: secrets, zod validation, uploads, SQL injection, httpOnly cookies, authorization, Supabase RLS, XSS/CSP, CSRF, rate limiting, logging/error hygiene, dependency hygiene, security tests, pre-deploy checklist; cloud/IAM/CI/WAF/backups reference.
- Weak at / risks: checklist-style, so it can miss app-specific logic flaws; some CSRF advice assumes a custom token lib; the cloud reference is AWS-heavy.
- Alternatives: OWASP ASVS and Top 10; the built-in /security-review command for diffs; rea-reverse-engineering for dependency behavior.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
