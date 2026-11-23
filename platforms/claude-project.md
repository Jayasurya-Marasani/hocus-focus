# Claude.ai Setup (Claude Projects)

Claude Projects natively supports uploading `SKILL.md` and `references/` as Project Knowledge, and renders `diagram` (Mermaid) and `interactive` (single-file HTML) directly in **Claude Artifacts**.

## Setup Steps (30 Seconds)
1. Open **Claude.ai -> Projects -> Create Project**.
2. Name it **hocus-focus**.
3. Upload these files to **Project Knowledge**:
   - `skills/hocus-focus/SKILL.md`
   - `skills/hocus-focus/references/modes.md`
   - `skills/hocus-focus/references/exam-formats.md`
   - `skills/hocus-focus/references/clarity-ladder.md`
4. Paste the short directive below into **Project Instructions**.

---

### Copy-Paste Project Instructions

```text
Follow the `hocus-focus` skill specification in the uploaded `SKILL.md` and `references/` files for every study request in this project.

Non-negotiable defaults:
- Default mode is `exam` unless the user specifies another mode (`quick`, `deep`, `compare`, `feynman`, `flashcards`, `quiz`, `ste`, `diagram`, `interactive`, `video`, or combinations).
- Strictly source-grounded: explain only concepts present in the user's screenshots, PDFs, or slides. Never add off-syllabus material; mark gaps as [Not stated in slides].
- Write in ~80% ASD-STE100 clarity (short, active, direct sentences; one term per concept) and cite `[Slide X]` / `[p. Y]` on multi-page sources.
- Hard stop immediately after delivering the output — zero greetings, filler, or follow-up prompts.
- When `interactive` mode is requested, output a single self-contained HTML artifact with zero external dependencies.
```
