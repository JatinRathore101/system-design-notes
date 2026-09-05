Use this public YouTube video URL containing a computer science / software engineering tutorial

Your task is to turn the video's **publicly available transcript into high-quality summarized study notes**.

## IMPORTANT — DO NOT PROCESS THE VIDEO

* **DO NOT download the video.**
* **DO NOT watch or analyze the video.**
* **DO NOT download or process the video's audio.**
* **DO NOT perform speech-to-text transcription yourself.**
* **DO NOT use Claude credits/tokens to process the actual video.**
* Only obtain the video's **title** and **existing publicly available transcript/captions**.
* Prefer YouTube's existing transcript/captions, including auto-generated captions.
* If YouTube's transcript is inaccessible, use a free/public transcript source if available.
* If no free transcript is available, stop and tell me rather than downloading/processing the video.

## TASK

Once you have obtained the **video title and complete transcript**:

1. Read the **entire transcript**.
2. Understand the concepts being taught.
3. Convert the entire tutorial into **crisp, clean, structured study material**.
4. Do NOT merely summarize the video at a high level. The resulting notes should contain the actual knowledge and explanations necessary to study the topic later without watching the video.
5. Remove:

   * filler words
   * greetings/intros/outros
   * repeated statements
   * unnecessary conversational language
   * irrelevant tangents
   * transcript timestamps
   * caption formatting artifacts
6. Preserve all important technical information, concepts, terminology, examples, algorithms, trade-offs, and explanations from the transcript.
7. Correct obvious transcript errors when the intended technical meaning is clear.
8. Organize the material logically rather than blindly following the transcript's sentence-by-sentence structure.

## NOTE QUALITY

The output should feel like **professional computer-science study notes**, suitable for:

Use:

* Clear headings and subheadings
* Bullet points
* Numbered steps for processes/algorithms
* Tables where comparisons are useful
* Code blocks when the transcript contains code or when a short code example significantly improves understanding
* Definitions of important concepts
* Key takeaways
* Examples where they are present in the tutorial
* Time/space complexity where relevant
* Pros/cons and trade-offs where relevant

Keep the writing **concise but sufficiently explanatory**.

Do not add large amounts of information that was not covered in the transcript. You may add a small clarification when necessary to make an explanation technically correct or understandable, but clearly prioritize the content of the tutorial.

## MARKDOWN FILE

Create a `.md` file containing the complete study material.

The file must be created inside the `/notes` directory of this repo.

The filename must be based on the **exact video title**, with:

* Spaces replaced by `-`
* `.md` extension added
* Remove characters that are invalid/problematic in filenames if necessary

For example:

```text
Video title:
"System Design Tutorial - Load Balancing Explained"

Filename:
System-Design-Tutorial---Load-Balancing-Explained.md
```

## MARKDOWN STRUCTURE

- Keep the video title and video link in the top of markdown file
- Add date at the top of the file in this format:
  - `Date: DD MMM YYYY` (e.g. `Date: 06 Sep 2026`)
- Adapt the structure to the actual content. Do not force unnecessary sections.

## TOKEN/CREDIT EFFICIENCY

Be extremely mindful of Claude usage.

The workflow should be:

```text
YouTube URL
    ↓
Fetch TITLE
    ↓
Fetch existing PUBLIC TRANSCRIPT/CAPTIONS
    ↓
Claude processes ONLY the transcript
    ↓
Generate study notes
    ↓
Save as <video-title>.md
```

**Never use the video itself as input to Claude.**

Do not unnecessarily reproduce the raw transcript in the conversation. The final `.md` file should contain the **cleaned study material/notes**, not the raw transcript.

After successfully creating the file, give me only:

1. A short confirmation that it was created
2. The file path

If the transcript cannot be obtained through a free/public source, explain the problem briefly and do not process the video.
