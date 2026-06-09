# Curation Prompt — Daily AI News Digest

This is the prompt the scheduled Claude routine runs every morning to regenerate `index.html` and `ai-news.html`.

---

## Task

Regenerate `index.html` and `ai-news.html` (keep them identical) in this repository with fresh AI news. The two files share the same content; `index.html` is what GitHub Pages serves at the root.

## Workflow

1. **Get today's date.** Run `date -u +%Y-%m-%d` and use that as "today". Compute the 14-day cutoff = today − 14 days.
2. **Read `ai-news.html` as the HTML/CSS template.** Preserve:
   - The complete `<head>` (CSS, viewport meta, title structure)
   - The `<header>` block structure (just update the `Last updated` date to today)
   - The four `<h2>` section headers and their order: General AI News → AI in the Audit Profession → Models &amp; Tools → AI Governance &amp; Regulation
   - The `<footer>` text
   - The `<script>` block at the bottom (auto-reload at 09:00 SGT) — **do not modify this script**
   - All CSS classes (`.item`, `.why-it-matters`, `.tag`, `.tag-general`, `.tag-practice`, `.tag-models`, `.tag-governance`, `.source`, `.source-host`, etc.)
3. **Run multiple parallel `WebSearch` calls** to find news for each section. Sample queries:
   - General: "AI news this week", "frontier AI lab announcement", "AI funding deal recent"
   - Audit profession: "audit firm AI announcement", "Big 4 GenAI assurance", "PCAOB IAASB AI", "RSM BDO EY KPMG Deloitte AI"
   - Models &amp; tools: "LLM model release this week", "AI dev tool announcement", "Copilot Gemini Claude OpenAI launch"
   - Governance: "EU AI Act enforcement", "US state AI law", "NIST ISO 42001 AI governance"
4. **Pick items.** Strict rules:
   - **General, Models &amp; Tools, Governance:** sources must be dated within the last 14 days. If a date is unclear, skip.
   - **AI in the Audit Profession:** no date cap — use the most relevant recent AI news from the audit profession (could be months old if the news cycle is quiet). Do NOT use the phrase "peer-firm" in the public-facing copy.
   - Target count per section: General 5, Audit Profession 4–5, Models &amp; Tools 4, Governance 3.
5. **Write each item.** For every news item:
   - `<h3>` headline
   - 1–2 sentence summary; wrap key facts (numbers, model names, dates, dollar amounts) in `<strong>` tags
   - A `<div class="why-it-matters">` callout starting with `<strong>Why it matters:</strong>` — written in **neutral, third-person tone** about implications for AI-deploying teams, organisations, or the industry. **Do NOT** reference "our team", "our firm", "us", "we", "the DS team", "engagement partners", or any specific reader identity.
   - A `<span class="tag tag-X">` where X is `general` / `practice` / `models` / `governance` matching the section
   - A `<a class="source" href="...">Read source →</a>` link to the underlying article
   - A `<span class="source-host">domain · date</span>` showing the publication source and date
6. **Overwrite both files.** Write the new HTML to `ai-news.html`, then copy it to `index.html` so they stay identical.
7. **Commit and push.** Use commit message `Refresh AI news for YYYY-MM-DD` with today's date. Push to `main`.

## Tone rules (important)

The page is publicly hosted via GitHub Pages, so the language must be neutral:

- ✅ "Worth tracking as a leading indicator…"
- ✅ "Organisations with EU exposure are on twin-track planning…"
- ✅ "Audit-trail patterns will harden into expectations…"
- ❌ "Our team should…", "We need to…", "Engagement partners will ask…", "Mid-tier audit firm…"

Audience is anyone interested in AI developments — write for that audience, not for a specific role or organisation.

## Style anchors

If you need a style reference, the existing `ai-news.html` in the repo is the template — match its tone, sentence length, and "Why it matters" phrasing.
