---
name: autoresearch
description: "Run Andrej Karpathy's autoresearch - a coding agent autonomously experiments on a small GPT training setup overnight (edit train.py, train 5 minutes, keep or discard by validation bits-per-byte) - safely in an isolated GPU environment. Use when Dean wants to try autonomous AI research loops, learn how LLM training improvements are found, run an overnight agent experiment on a rented GPU, or mentions autoresearch."
metadata:
  pricing: pay-per-use
  cost: "Software free (MIT). Needs a single NVIDIA GPU (tested on H100), usually rented by the hour (a few dollars an hour, not verified), plus agent usage (Claude subscription or API) for an overnight run."
  tags: [ml-research, llm-training, autonomous-agents, gpu, experiments]
---

# autoresearch

[karpathy/autoresearch](https://github.com/karpathy/autoresearch) (MIT) has three files that matter: `prepare.py` (fixed data and tokenizer setup), `train.py` (the GPT model and training loop, the **only file the agent edits**) and `program.md` (the agent's instructions, edited by the human). Each experiment trains for a fixed **5 minutes**. The metric is **val_bpb** (lower is better), and the agent keeps or discards each change and repeats.

## Is it for Dean?

It's a research and learning toy, not a web-dev tool. Run it to understand agentic research loops, or for fun on a rented GPU. It doesn't help ship client sites. There's no Mac/CPU path for real results: it needs an NVIDIA GPU (tested on H100).

## Run it safely

The README says to start the agent with **all permissions disabled** and let it loop overnight. Only do that in an **isolated, disposable environment**:
- A rented cloud GPU VM or container with nothing else on it: no client code, no SSH keys or cloud credentials beyond what it needs, no access to Dean's accounts.
- Keep it in its own git repo, and let the agent commit experiments so every change is reviewable.
- Budget: set a stop time (for example 8 hours), and shut the GPU instance down afterwards. A forgotten H100 is expensive.
- Never run permission-free agents on Dean's main machine.

## Quick start (on the GPU box)

```bash
# Install uv from its official docs (the README's `curl … | sh` is download-and-execute; read it first or use pipx/brew)
uv sync
uv run prepare.py      # one-time data + tokenizer (~2 min)
uv run train.py        # one manual 5-minute run to verify the setup
```

Then open Claude Code in the repo and prompt: "Read program.md and start a new experiment; do the setup first." In the morning, review `git log`, the results chart and which changes were kept.

## What to take from it

The pattern works for other domains too: a fixed budget per try, one clear metric, one editable file, keep-or-revert, and a human-written `program.md`. For example, Lighthouse score tuning on a static site, with the same isolation rules.
