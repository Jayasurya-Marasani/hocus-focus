# hocus-focus — Mode Specifications

All modes inherit the Core Guardrails in `SKILL.md`: strict source grounding, `[Slide X]` / `[p. Y]` tagging when multi-page, ~80% ASD-STE100 clarity, and **hard stop** immediately after the output.

---

## Core Modes

### `exam` (Default)
Brief, sufficient, exam-testable breakdown. No textbook essays.

**Output Template:**
```markdown
### <Topic Name> [Slide X]
**Core Idea:** 1–2 direct sentences defining the concept.

**Key Points:**
- **<Keyword>:** Crisp testable fact or mechanism. [Slide X]
- **<Keyword>:** Crisp testable fact or mechanism. [Slide X]
- **<Keyword>:** Crisp testable fact or mechanism. [Slide Y]

**Formula / Mechanism** *(include only if present in source)*:
- `<formula>` — define each symbol in one line.
```

**Rules:**
- Bold the exact terms a grader looks for.
- Keep total bullets tight (typically 3–7 per topic).
- Omit any section not supported by the source material.

---

### `quick` (3–5 Bullets)
Maximum compression for dense, repetitive, or image-heavy slides.

**Output Template:**
```markdown
### <Topic / Slide Name> [Slide X]
- **<Term>:** One-line takeaway.
- **<Term>:** One-line takeaway.
- **<Term>:** One-line takeaway.
```

**Rules:**
- Strictly **3 to 5 bullets** per slide or sub-topic.
- Zero introductory or concluding paragraphs.
- One idea per bullet; maximum ~20 words per bullet unless a formula requires more.

---

### `deep` (Strict Detailed)
Complete explanation of **every** concept present in the source — thorough, structured, and strictly bounded to the uploaded material.

**Rules:**
- Cover every definition, condition, edge case, assumption, step, and sub-point shown in the slides/PDF.
- Organize with clear subheadings matching the source flow.
- Do **not** pad with outside history, anecdotes, or off-syllabus examples.
- If the source omits an intermediate step or definition, mark `[Not stated in slides]` rather than inventing it.

---

## Study Extra Modes (Strictly On-Demand)

Never produce these unless the user explicitly asks.

### `compare` (Comparison Table)
Best for short-answer and essay *"Compare / Contrast X vs. Y"* questions.

**Output Template:**
```markdown
| Dimension | <Concept A> | <Concept B> |
| :--- | :--- | :--- |
| **Core Mechanism** | ... [Slide X] | ... [Slide Y] |
| **Key Advantage** | ... | ... |
| **Limitation / Condition** | ... | ... |
```

**Rules:**
- Include only dimensions supported by the source.
- Mark missing cells as `Not stated in slides` instead of guessing.

---

### `feynman` (Plain-Language Intuition)
Simple cause-and-effect explanation for a difficult concept from the slides.

**Rules:**
- Explain in plain, everyday words using short active sentences.
- Keep the mental model **100% faithful** to the source's scope — do not introduce outside concepts that contradict or exceed the syllabus.
- End with a 1-line **Exam Phrasing** block mapping the simple intuition back to the exact technical terms from the slide.

---

### `flashcards` (Active Recall Cards)
Source-grounded Q&A cards.

**Output Template (Default Markdown):**
```markdown
1. **Q:** <Direct testable question> [Slide X]
   **A:** <Concise 1–2 line answer with exact keywords>
```

**Anki TSV Option:** If the user asks for `anki` or `tsv`, output a single fenced `tsv` code block (`Front<TAB>Back`) with no extra prose.

---

### `quiz` (Source-Grounded Practice)
Exam-style questions drawn strictly from the provided material.

**Rules:**
- Default to 3–5 questions matching the user's exam style (short-answer, derivation, or essay prompt) unless the user specifies a count.
- Put all questions first, followed by a `---` divider and a **Concise Answer Key** with `[Slide X]` citations.
- Stop immediately after the answer key.

---

## Combining Modes

Users can combine modes in one request (for example: `diagram + exam`, `quick + compare`, `deep + ste`).
- Apply **structure** from the primary format mode (e.g., `quick`, `exam`, `diagram`).
- Apply **style/output** modifiers cleanly without repeating the same points twice.
