# CLAUDE.md

## About This Repo

This is a **multi-topic notes repo** — markdown tutorial notes for whatever CS topic I am studying (`system-design`, `lld`, aur aage jo bhi add ho). Every file is a self-contained tutorial/notes file based on one video/topic.

## Topics & Index Files

- Har note ek **topic** se belong karta hai. Topic slug hamesha **lowercase kebab-case**, no spaces — `system-design`, `lld`, `dbms`.
- Agar topic input kisi aur form me mile (`System Design`, `system_design`), toh normalize karo: lowercase karo → non-alphanumeric chars ko `-` se replace karo → repeated `-` collapse karo → aage-peeche ke `-` hata do.
- **Topic display name** = slug ke saare non-alphanumeric chars ko space se replace karo aur poora UPPERCASE kar do. Example: `system-design` → `SYSTEM DESIGN`.
- **Notes hamesha flat `notes/` folder me** rehte hain — topic-wise subfolder kabhi mat banao.
- Har topic ka apna index file repo root pe: **`<topic-slug>.table.md`** (e.g. `system-design.table.md`, `lld.table.md`).
- Index file ka format fix hai — `# <TOPIC DISPLAY NAME>` heading, phir ye table:

  ```markdown
  # SYSTEM DESIGN

  | # | Date | Title | Link to video | Link to file |
  |---|------|-------|---------------|--------------|
  | 1 | 05 Sep 2026 | <Video Title> | [Watch](<youtube-url>) | [Open notes](./notes/<filename>.md) |
  ```

- Naya note banne pe us topic ki table file me **sirf ek nayi row append** karo (`#` last row se +1). Existing rows ko na edit karo, na reorder.
- Topic ki table file exist nahi karti toh nayi banao — heading + table header + row `1`.
- **Naya topic** banaya ho toh `README.md` ke "Notes Index" table me bhi us topic ki ek row add kar do. Purana topic hai toh README ko haath mat lagao.

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

- Notes ki files hamesha `notes/` folder me.
- File names: `kebab-case.md` (e.g. `load-balancing.md`, `cap-theorem.md`, `url-shortener-hld.md`). YouTube video se bana note ho toh video title based naam (spaces → `-`) bhi theek hai.
- One topic per file. Bade topics ko split karo instead of one giant file.
- Related topics ko link karo: `[Caching](./caching.md)`.
- Har note file ka header ye standard format follow kare — H1 title ke baad Topic / Video / Date ka bullet block:

  ```markdown
  # <Note ya Video Title>

  - **Topic:** SYSTEM DESIGN
  - **Video:** [<Video Title>](https://www.youtube.com/watch?v=...)
  - **Date:** 06 Sep 2026
  ```

  - `Topic` hamesha display name (UPPERCASE) form me.
  - `Video` line sirf tab jab note kisi video se bana ho.
  - `Date` format: `DD MMM YYYY`.
