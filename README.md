# System Design Notes 📚

- Ye repo **System Design** aur **HLD (High Level Design)** topics ke markdown tutorial notes ka collection hai.
- Notes **simple Hinglish** me likhe gaye hain — friend ko samjhane wale style me, short crisp bullet points ke saath.
- Zyada tar notes YouTube tutorials (jaise ByteByteGo) ke transcripts se bane hain.

## Repo Structure

```text
system-design/
├── notes/      # Saare tutorial notes (ek topic = ek file)
├── prompt/     # YouTube video → notes banane wala reusable prompt
├── table.md    # Saare notes ka index (date, title, video link, file link)
└── CLAUDE.md   # Notes likhne ke rules (language, tone, formatting)
```

## Notes Index

- Saare notes ki list ek jagah dekhni ho toh **[table.md](./table.md)** kholo.
- Har note ke saath uska date, original video link aur file ka clickable link milega.

## Naya Note Kaise Banate Hain?

1. YouTube video ka URL lo.
2. [youtube-link-to-notes-prompt.md](./prompt/youtube-link-to-notes-prompt.md) wala prompt Claude Code me use karo (URL ke saath).
3. Prompt automatically:
   - Video ka **title aur public transcript** fetch karta hai (video download nahi hota).
   - Transcript ko clean, structured study notes me convert karta hai.
   - `notes/` folder me `<video-title>.md` file banata hai.
   - `table.md` me nayi row add karta hai.

## Notes ka Format

- Har file self-contained hai — ek topic, ek file.
- File ke top pe video title, video link aur date hota hai.
- Style: short bullets, tables for comparisons, mermaid/ASCII diagrams jahan helpful ho.
- Detailed writing rules ke liye [CLAUDE.md](./CLAUDE.md) dekho.
