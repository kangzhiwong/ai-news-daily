# AI News Digest

A self-refreshing daily digest of AI news across four lenses: general industry signals, the audit profession, models &amp; tools, and governance.

**Live page:** https://kangzhiwong.github.io/ai-news-daily/

## How the refresh works

- A scheduled Claude Code routine runs every day at **08:30 SGT (00:30 UTC)** — early enough that regeneration + GitHub Pages rebuild finishes before users see the page at 09:00.
- The routine clones this repo, re-runs the curation prompt in [`curation-prompt.md`](./curation-prompt.md), regenerates `index.html` / `ai-news.html` with fresh items, and commits + pushes the result.
- GitHub Pages serves the latest `index.html` at the URL above.
- The HTML itself contains a small JS snippet that reloads the page at **09:00 SGT** each day, so a tab left open will pick up the new content automatically.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Page served at the GitHub Pages root (identical to `ai-news.html`) |
| `ai-news.html` | Canonical copy of the page |
| `curation-prompt.md` | Self-contained instructions the scheduled Claude routine follows to regenerate the page |

## Section structure

1. **General AI News** — broader industry signals from the last 14 days
2. **AI in the Audit Profession** — activity in the audit profession (no date cap; uses most recent relevant items)
3. **Models &amp; Tools** — frontier-model releases and dev tooling from the last 14 days
4. **AI Governance &amp; Regulation** — laws, frameworks, standards from the last 14 days

Each item has a 1–2 sentence summary with bolded key facts, a "Why it matters" callout, a colored tag, and a source link with publication date.
