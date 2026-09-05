# CLAUDE.md

## About This Repo

This repo stores markdown tutorial notes for **System Design** and **HLD (High Level Design)** topics. Every file is a self-contained tutorial/notes file on one topic.

## Language & Tone (MOST IMPORTANT)

- Write in **simple Hinglish** — Hindi + English mix, written in English (Latin) script. NOT plain formal English.
- Example of the expected tone:
  - ❌ "Load balancing is a technique that distributes incoming network traffic across multiple servers to ensure reliability."
  - ✅ "Load balancer ka kaam simple hai — aane wali requests ko multiple servers me baant do, taaki koi ek server overload na ho."
- Explain like you're explaining to a friend, layman style. Technical terms (cache, sharding, replica, throughput etc.) English me hi rakho — unka Hindi translation mat karo.
- Avoid jargon-heavy sentences. Agar koi jargon use karna zaroori hai, toh ek line me simple meaning bata do.

## Content Rules

- **Short, crisp bullet points** — no long story-style paragraphs. Max 1-2 lines per point.
- **Summarized but complete** — content chhota rakho, lekin koi important detail (trade-offs, numbers, edge cases, "kab use karna hai / kab nahi") kabhi skip mat karo.
- No filler intro/outro text ("In this tutorial we will learn...", "Hope you enjoyed..."). Seedha point pe aao.
- Prefer bullets, tables, and diagrams over paragraphs. Paragraph sirf tab jab genuinely zaroori ho (max 2-3 lines).

## Markdown Formatting Rules

Every file must be **proper markdown**, not plain text:

- One `# H1` title at the top, then `##` / `###` for sections.
- Bullet points (`-`) for lists, numbered lists (`1.`) for steps/flows.
- **Bold** for key terms on first use, `inline code` for technical names (APIs, commands, config values).
- Tables for comparisons (e.g. SQL vs NoSQL, Push vs Pull).
- Fenced code blocks (with language tag) for code, configs, or API examples.
- ` ```mermaid ` blocks or ASCII diagrams for architecture flows where helpful.
- **ER diagrams** (` ```mermaid ` + `erDiagram`) for DB schema/relationships — sirf tab use karo jab genuinely zaroori ho aur doc ki quality improve kare (e.g. HLD me database design section). Har file me forcefully mat daalo.
- **Mermaid tables/entity blocks** for table structures (columns, types, keys) — jab schema ka detail dikhana ho aur normal markdown table se baat clear na ho. Necessary ho tabhi use karo, warna simple markdown table hi kaafi hai.
- Blockquotes (`>`) for important notes / gotchas / interview tips.

## Suggested File Structure

A typical tutorial file should roughly follow (adapt as needed per topic):

```markdown
# Topic Name

## Kya hai ye? (What & Why)
- 2-4 crisp points

## Kaise kaam karta hai? (How it works)
- Core concept points / flow / diagram

## Key Components / Types
- Bullets or table

## Trade-offs / Pros & Cons
- Table ya bullets

## Kab use karein, kab nahi
- Real-world scenarios

> Interview tip / gotcha (agar relevant ho)
```

## File Conventions

- File names: `kebab-case.md` (e.g. `load-balancing.md`, `cap-theorem.md`, `url-shortener-hld.md`).
- One topic per file. Bade topics ko split karo instead of one giant file.
- Related topics ko link karo: `[Caching](./caching.md)`.
