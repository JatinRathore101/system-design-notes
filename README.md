# My Notes 📚

- Ye repo alag-alag CS topics (**System Design**, **LLD**, aur aage jo bhi add ho) ke markdown tutorial notes ka collection hai.
- Notes **simple Hinglish** me likhe gaye hain — friend ko samjhane wale style me, short crisp bullet points ke saath.
- Zyada tar notes YouTube tutorials (jaise ByteByteGo) ke transcripts se bane hain.

## Repo Structure

```text
my-notes/
├── notes/               # Saare tutorial notes (ek video = ek file, sab topics ek hi folder me)
├── prompt/              # YouTube video → notes banane wala reusable prompt
├── <topic>.table.md     # Per-topic index (date, title, video link, file link)
└── CLAUDE.md            # Notes likhne ke rules (language, tone, formatting)
```

- Notes kabhi topic-wise subfolder me nahi jaate — sab flat `notes/` me rehte hain.
- Topic ka alag hona sirf **index file** se pata chalta hai: `system-design.table.md`, `lld.table.md`, waghairah.

## Notes Index

Har topic ka apna index file hai — usme us topic ke saare notes ki list (date, title, video link, file link) milegi.

| Topic | Index |
|-------|-------|
| SYSTEM DESIGN | [system-design.table.md](./system-design.table.md) |

## Naya Note Kaise Banate Hain?

1. YouTube video ka URL lo aur decide karo ye kis **topic** ka hai (e.g. `system-design`, `lld`).
2. [youtube-link-to-notes-prompt.md](./prompt/youtube-link-to-notes-prompt.md) wala prompt Claude Code me use karo — URL **aur** topic name ke saath.
3. Prompt automatically:
   - Video ka **title aur public transcript** fetch karta hai (video download nahi hota).
   - Transcript ko clean, structured study notes me convert karta hai.
   - `notes/` folder me `<video-title>.md` file banata hai.
   - `<topic>.table.md` me nayi row add karta hai (file na ho toh nayi bana deta hai).
   - Topic bilkul naya ho toh upar wale **Notes Index** table me bhi ek row add kar deta hai.

## Notes ka Format

- Har file self-contained hai — ek video, ek file.
- File ke top pe topic, video link aur date hota hai:

  ```markdown
  # <Video Title>

  - **Topic:** SYSTEM DESIGN
  - **Video:** [<Video Title>](https://www.youtube.com/watch?v=...)
  - **Date:** 06 Sep 2026
  ```

- Style: short bullets, tables for comparisons, mermaid/ASCII diagrams jahan helpful ho.
- Detailed writing rules ke liye [CLAUDE.md](./CLAUDE.md) dekho.
