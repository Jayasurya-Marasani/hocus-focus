# hocus-focus — Exam Format Rules

Adapt the explanation structure automatically when the material or user indicates a specific exam type. Keep all content strictly grounded in the provided slides, PDFs, or screenshots, and stop cleanly at the end.

---

## 1. Short-Answer Exams

**Goal:** Give exact definitions, keywords, and high-yield points that earn full marks in 2–5 lines.

**Structure:**
- **Definition:** 1 direct sentence using the source's exact terminology.
- **Scoring Points:** 3–5 concise bullets; **bold** every gradable keyword, condition, or threshold.
- **Key Distinction** *(only if the source contrasts two terms)*: 1 line stating what separates them.

**Avoid:** Long background paragraphs, vague phrasing, or swapping technical terms for synonyms.

---

## 2. Derivations & Math Exams

**Goal:** Show exact logical progression from assumptions to final result with zero prose bloat.

**Structure:**
1. **Given / Assumptions:** List starting equations, constraints, and boundary conditions from the source. `[Slide X]`
2. **Symbols:** One-line legend for variables/constants (only those used).
3. **Derivation Steps:** Numbered steps in `Action -> Equation` form:
   - Step 1: <Operation applied> -> `<equation>`
   - Step 2: <Substitution / simplification> -> `<equation>`
4. **Final Result & Condition:** Box or bold the final formula and state when it holds (strictly from the source).

**Rules:**
- Never skip an algebraic or logical jump that appears in the source.
- If the source skips intermediate algebra and the user asks for `deep`, show only the standard algebraic rearrangement of the source's equations without adding new physical/theoretical assumptions; otherwise mark `[Skipped in slides]`.

---

## 3. Essay Exams

**Goal:** Provide a crisp, high-signal argument skeleton the student can expand into full paragraphs under exam time pressure.

**Structure:**
- **Core Thesis / Claim:** 1–2 sentences capturing the central concept or argument. `[Slide X]`
- **Key Mechanisms / Arguments:** 3–5 numbered points, each formatted as:
  - **<Point Title>:** Cause -> Mechanism -> Effect (using source evidence/examples only).
- **Counterpoints / Limitations / Trade-offs** *(only if present in source)*: 1–3 crisp bullets.

**Avoid:** Writing a full 500-word mock essay unless the user explicitly asks for a sample essay.

---

## 4. General-Purpose Fallback

When no exam format is specified and the slide is mixed:
- Use **`exam` mode** (`Core Idea` + `Key Points` + `Formula / Mechanism` if present).
- Keep definitions sharp enough for short-answer, steps clear enough for math, and cause-effect links clear enough for essays.
