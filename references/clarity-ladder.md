# hocus-focus — Karpathy's 4-Level Clarity Ladder

Use these four progressive formats when the user wants higher-clarity explanations beyond standard bullets. All four levels still obey strict source grounding and hard stop.

---

## Level 1: `ste` — ASD-STE100 Controlled Language (~80% Adherence)

Inspired by aerospace Simplified Technical English (ASD-STE100) for maximum precision and minimum cognitive load.

**Writing Rules:**
1. **Short sentences:** Aim for 10–20 words per sentence. Split long multi-clause sentences into two direct sentences.
2. **Active voice:** Put the actor first (`The router drops the packet`, not `The packet is dropped by the router`).
3. **One word per meaning:** Pick one exact technical term from the source and reuse it consistently. Do not cycle through synonyms.
4. **Direct verbs:** Replace nominalizations (`perform an evaluation of` -> `evaluate`, `make a comparison` -> `compare`).
5. **~80% adherence:** Preserve natural readability and exact syllabus terms — never make the text feel stiff or robotic.

**When to apply:**
- **Always** as the subtle baseline style across all `hocus-focus` modes.
- **Strictly** when the user requests `ste`, `aerospace`, or `plain` mode.

---

## Level 2: `diagram` — Visual-First Understanding

Handles **both** reading image-heavy slides and turning dense text into scannable visuals.

### Case A: Input is an Image-Heavy Slide / Screenshot
Output:
1. **What This Visual Shows:** 1 direct sentence summarizing the diagram's purpose. `[Slide X]`
2. **Core Relationships (3–5 Bullets):** Trace the flow, hierarchy, inputs -> outputs, or axes directly from the visual.
3. **Exam-Testable Callouts** *(include when present in the visual or requested by user)*:
   - Key formulas, thresholds, labels, or comparisons likely to be tested.

### Case B: Input is Dense Text / Process / Architecture
Convert the text into a clean diagram **instead of paragraphs**:
- Prefer **Mermaid** (`flowchart TD`/`LR`, `sequenceDiagram`, `stateDiagram-v2`, `classDiagram`) when the platform renders Mermaid.
- Fall back to clean **ASCII** diagrams if the user asks for plain text or the chat UI does not render Mermaid.
- Quote Mermaid labels containing parentheses or brackets (`A["Label (Info)"]`).
- Follow the diagram with at most 3 ultra-short bullet takeaways if needed, then hard stop.

---

## Level 3: `interactive` — Standalone Interactive HTML Page

Build a hands-on, single-file HTML/CSS/JS learning artifact grounded strictly in the uploaded topic (for example: formula calculator with sliders, step-through derivation viewer, interactive state machine, or parameter-effect plot).

**Requirements:**
1. **Single self-contained file:** Inline `<style>` and `<script>` inside one `.html` document. Zero external CDN dependencies so it runs offline and works cleanly in Claude Artifacts, ChatGPT Canvas, Gemini Canvas, or any local browser.
2. **Strict source grounding:** Every variable, equation, label, and state must come directly from the user's slides/PDF.
3. **Exam-focused interactivity:**
   - Sliders or numeric inputs that update outputs/visuals in real time.
   - Or a **Step-by-Step** button (`Prev / Next`) for derivations, algorithms, or multi-stage processes.
   - Clear display of the exact formula/rule currently being demonstrated.
4. **Clean, scannable UI:** Minimalist layout, high contrast, readable typography, responsive on desktop and mobile.
5. **Delivery:**
   - In coding agents (Claude Code, Codex, Gemini CLI, Cursor, Antigravity): save to a clear filename (e.g., `<topic>-interactive.html`) if the user is in a workspace, or output the complete HTML block if they only asked in chat.
   - In web chats: output the complete single HTML code block directly so Artifacts/Canvas can render it immediately.
   - Stop cleanly right after delivering the HTML.

---

## Level 4: `video` — Custom 3Blue1Brown-Style Explainer Package

Create a bespoke visual explainer blueprint (and runnable animation code) for a topic from the slides.

**Output Structure:**
1. **Concept Hook (1 line):** The exact visual intuition the explainer builds. `[Slide X]`
2. **Scene-by-Scene Storyboard (3–6 Scenes):**
   | Scene | Duration | Visual On Screen | ASD-STE100 Narration Script |
   | :--- | :--- | :--- | :--- |
   | 1 | 0:00–0:15 | ... | Short, crisp voiceover line. |
3. **Runnable Manim Scene (`manim` Community Edition):**
   - Provide a clean, self-contained Python `Scene` class implementing the key visual transformation/derivation from the storyboard.
   - Add inline comments (`# [VO]: ...`) mapping each animation step to its narration cue so the user can pair it with any TTS or voiceover tool (such as `manim-voiceover`, Edge TTS, ElevenLabs, or manual recording).
   - Keep objects, labels, and equations strictly faithful to the user's slides.
4. **Render Command (1 line):**
   - `manim -pql <file>.py <SceneName>`
5. **Hard Stop:** No extra chatter after the render command.
