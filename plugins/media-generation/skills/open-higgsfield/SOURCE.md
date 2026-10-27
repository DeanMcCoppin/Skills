# Source

- Tool: https://github.com/wide-trace/open-higgsfield (author: wide-trace)
- Reviewed commit: b16a0ef (2026-09-17). Read-only review on 2026-10-27: the key is sent as `Authorization: Key id:secret` only to `HF_API_BASE_URL`; a search of `src/` found no other hard-coded hosts besides Vercel Blob uploads, and no telemetry. Not a full audit.
- Tool license: **none**. This skill only links to the tool and describes how to use it; no code from it is included here.
- Skill text: Dean (original), written with Claude. License: TODO (this repo has no LICENSE file yet).
- Notes: about 4.8k stars against 3 commits at review time. Re-review before updating the pinned commit.
