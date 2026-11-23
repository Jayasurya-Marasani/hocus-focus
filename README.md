# hocus-focus

An open-source, cross-platform **Agent Skill** that turns dense lecture slides, screenshots, PDFs, and PPTs into **brief, concise, exam-ready explanations** — strictly grounded in your course material, with zero fluff.

Built on the open [`agentskills.io`](https://agentskills.io) `SKILL.md` standard so it works natively across **Claude Code, OpenAI Codex, Gemini CLI, Cursor, Antigravity**, and other coding/agent tools — plus ready-to-paste presets for **ChatGPT, Gemini Gems, Claude Projects, and any free web LLM**.

---

## Why `hocus-focus`?

When you paste lecture slides into an LLM and ask for an *"exam point of view"* explanation, it usually dumps a long textbook essay full of off-syllabus trivia and filler.

`hocus-focus` enforces five always-on rules:
1. **Strict Source Grounding** — Explains *only* the concepts, definitions, formulas, and relationships in your uploaded material. Marks missing info as `[Not stated in slides]` instead of hallucinating.
2. **Hard Stop (Zero Chatter)** — No greetings, no filler, no unsolicited quizzes or follow-up questions. Stops immediately after the explanation.
3. **Source Traceability** — Tags points with `[Slide X]` or `[p. Y]` on multi-page inputs so you can verify everything against your slides.
4. **Aerospace Clarity (~80% ASD-STE100)** — Short, active, direct sentences with one consistent term per concept.
5. **Exam-Format Aware** — Adapts cleanly to **short-answer**, **derivations/math**, and **essay** exams.

---

## Mode Cheat Sheet

Pick any mode — or combine them (e.g., `diagram + exam`, `quick + compare`). **Defaults to `exam`** if you don't name a mode.

### Core Modes
| Mode | Use When | Output |
| :--- | :--- | :--- |
| **`exam`** *(default)* | Normal exam prep | Core idea (1–2 lines) + testable points with **bold** keywords + formula/mechanism if present. |
| **`quick`** (`bullets`) | Dense or repetitive slides | Strictly **3–5 one-line bullets** per slide/topic. Zero paragraphs. |
| **`deep`** | You want every detail in the slides | Full structured breakdown of every concept strictly inside your material. |

### Study Extras *(Strictly On-Demand)*
| Mode | Use When | Output |
| :--- | :--- | :--- |
| **`compare`** (`table`) | "Compare X vs. Y" questions | Compact Markdown comparison table from source dimensions. |
| **`feynman`** (`simple`) | A slide concept feels abstract | Plain cause-and-effect intuition + 1-line Exam Phrasing. |
| **`flashcards`** (`anki`) | Active recall / Anki import | Source-grounded Q/A cards (or Anki TSV block). |
| **`quiz`** (`test me`) | Self-testing before an exam | 3–5 source-grounded exam questions + separated Answer Key. |

### 4-Level Clarity Ladder *(Inspired by Andrej Karpathy)*
| Level | Mode | Output |
| :--- | :--- | :--- |
| **L1** | **`ste`** | Strict ~80% ASD-STE100 aerospace-clarity rewrite. |
| **L2** | **`diagram`** | **Image-heavy slides:** 1-line visual summary + 3–5 relationship bullets (+ testable formulas/comparisons). **Dense text:** clean Mermaid or ASCII diagram instead of paragraphs. |
| **L3** | **`interactive`** (`html`) | Standalone single-file HTML/CSS/JS interactive explorer (sliders, formula calculator, or step-by-step viewer) with zero external CDNs. |
| **L4** | **`video`** (`3b1b`) | 3Blue1Brown-style explainer: concept hook, 3–6 scene storyboard + ASD-STE100 narration, runnable **Manim** Python scene with `# [VO]` cues, and render command. |

### Example Prompts
- *(Paste screenshot)* -> Uses **`exam`** mode automatically.
- `quick` *(paste 10 slides)* -> 3–5 bullets per slide with `[Slide X]` tags.
- `diagram + exam` *(paste architecture screenshot)* -> Visual breakdown + exam-testable takeaways.
- `deep` *(paste math derivation PDF)* -> Step-by-step `Given -> Step -> Result` strictly from the PDF.
- `interactive` *(paste physics/CS formula slide)* -> Single-file HTML simulator with sliders.
- `video` *(paste complex algorithm slide)* -> Storyboard, narration script, and runnable Manim scene.

---

## 30-Second Setup

### 1. Agentic CLI & IDE Tools (Claude Code, Codex, Gemini CLI, Cursor, Antigravity)

**Option A — Universal Agent Skills CLI (`skills.sh`):**
```bash
npx skills add Jayasurya-Marasani/hocus-focus
```

**Option B — Claude Code Plugin Marketplace:**
```bash
/plugin marketplace add Jayasurya-Marasani/hocus-focus
/plugin install hocus-focus@hocus-focus
```

**Option C — Manual Drop-In:**
Copy `skills/hocus-focus/` into your agent's skills directory (for example `~/.claude/skills/hocus-focus/`, `~/.codex/skills/hocus-focus/`, or `~/.gemini/skills/hocus-focus/`).

### 2. Web Chat LLMs (No Terminal Needed)
Use the ready-to-paste presets in [`platforms/`](./platforms/):
- **ChatGPT (Custom GPT / Custom Instructions):** [`platforms/chatgpt-custom-gpt.md`](./platforms/chatgpt-custom-gpt.md)
- **Google Gemini (Gems):** [`platforms/gemini-gem.md`](./platforms/gemini-gem.md)
- **Claude.ai (Claude Projects):** [`platforms/claude-project.md`](./platforms/claude-project.md)
- **Any Free LLM Chat** *(DeepSeek, Perplexity, Grok, Mistral, Ollama, etc.)*: [`platforms/universal-prompt.md`](./platforms/universal-prompt.md)

---

## Repository Structure

```text
hocus-focus/
├── .claude-plugin/
│   ├── marketplace.json          # Claude Code plugin marketplace manifest
│   └── plugin.json               # Claude Code plugin manifest
├── skills/
│   └── hocus-focus/
│       ├── SKILL.md              # Agent Skills open-standard entrypoint
│       └── references/
│           ├── modes.md          # Core & on-demand study mode specs
│           ├── exam-formats.md   # Short-answer, derivations/math, & essay rules
│           └── clarity-ladder.md # Karpathy 4-level ladder (STE100, Diagram, HTML, Video)
├── platforms/
│   ├── chatgpt-custom-gpt.md     # ChatGPT Custom GPT / Custom Instructions
│   ├── gemini-gem.md             # Gemini Gem setup & directive
│   ├── claude-project.md         # Claude Projects setup & directive
│   └── universal-prompt.md       # Copy-paste prompt for any LLM
├── README.md
└── LICENSE                       # MIT
```

---

## Acknowledgements & Inspiration

All instructions, templates, and prompts in `hocus-focus` are original work licensed under the [MIT License](./LICENSE).

- **[Sneharajalakshmi Palanisamy](https://github.com/sneharajalakshmi)** — For suggesting the name **`hocus-focus`**.
- **[Agent Skills (`agentskills.io`)](https://agentskills.io)** — Open standard for portable `SKILL.md` skills and progressive disclosure.
- **Andrej Karpathy's Four-Level Understanding Ladder** — Combining ASD-STE100 controlled language, diagrams, standalone interactive HTML pages, and custom explainer videos for clearer LLM explanations.
- **ASD-STE100 (Simplified Technical English)** — Aerospace technical writing discipline for short, active, unambiguous sentences.
- **Open-source study skill workflows** — General pedagogical patterns such as strict source grounding, citation tagging, Feynman intuition, and on-demand active recall.
