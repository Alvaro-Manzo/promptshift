# promptshift

[![MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-active-brightgreen.svg)]()
[![Made for Claude Skills](https://img.shields.io/badge/made%20for-Claude%20Skills-blueviolet.svg)]()

> Model-aware prompt adapter for Claude — translate any prompt to GPT, Gemini, Mistral, Llama and more.

Prompts built for one model fail silently on another. promptshift is a Claude skill that takes any prompt, applies model-specific transformation rules, runs a repair pass, and returns a scored before/after result — ready to copy-paste.

---

## How it works

1. **Triage** — classifies the prompt as simple or complex
2. **Pattern detection** — identifies zero-shot, few-shot, CoT, role-based, ReAct, tool-calling, RAG, or hybrid
3. **Task classification** — labels the task type (reasoning, coding, writing, extraction, agent, multimodal…)
4. **Model adaptation** — applies model-specific rules from the knowledge base
5. **Repair pass** — fixes ambiguities, weak constraints, contradictions, and missing examples
6. **Scored output** — returns ANALYSIS + OPTIMIZED PROMPT + CHANGES + numeric SCORE

---

## Installation

```bash
git clone https://github.com/Alvaro-Manzo/promptshift.git
```

1. Copy `skill/SKILL.md` into the Claude Skills import UI, or register it via the Claude SDK
2. Confirm the skill is enabled and that trigger phrases from the frontmatter are active
3. Optionally add `examples/examples.md` to your project for team reference

**Trigger phrases (any of these activate the skill):**
`"optimize this prompt"` · `"adapt for [model]"` · `"rewrite for [model]"` · `"this prompt is for [model]"` · `"make this work on [model]"` · `"prompt isn't performing on [model]"`

---

## Usage example

**Input prompt:**
```
Summarize the attached article about recent climate policy developments
and their implications for global emissions.
```
**Target model:** Gemini 2.5 Pro

---

### ANALYSIS
Zero-shot prompt, no audience, no output structure, no length constraint. Pattern: zero-shot / summarization. Complexity: SIMPLE.

### OPTIMIZED PROMPT
```
Act as an expert policy analyst. Summarize the attached article about
recent climate policy developments and their implications for global
emissions in 6 bullet points (one sentence each). Include one short
(2-sentence) takeaway for policymakers and one quantified key risk or
uncertainty. Use imperative bullet labels. Total length: under 200 words.
```

### CHANGES
- Added role `expert policy analyst` → Gemini 2.5 Pro responds best to imperative role framing
- Converted to structured brief → explicit bullet count reduces ambiguity
- Added length constraint → prevents verbosity on Gemini
- Added policy takeaway and quantified risk → matches Gemini's strength for focused analytical output

### SCORE
| | |
|---|---|
| Before | 4 / 10 |
| After | 9 / 10 |
| Key gain | Explicit structure eliminates output variance |

---

## Supported models

| Family | Models | Prompt style |
|---|---|---|
| OpenAI | GPT-5.5, GPT-5.4, o3, GPT-4o | Role + explicit limits; anchor key instructions at end |
| Anthropic | Claude Opus 4.8 / Sonnet 4.6 | XML tags; explain WHY; CoT opt-in for hard tasks |
| Google | Gemini 2.5 Pro / Flash | Bullet/imperative instructions; explicit length constraints |
| xAI | Grok 4.3 / 4.1 | Conversational framing; real-time web context native |
| DeepSeek | R1, V4 Pro / Flash | No CoT scaffolding for R1; explicit format for V4 |
| Meta | Llama 4 Scout / Maverick, 3.3 | Few-shot preferred; short system prompt under 300 tokens |
| Mistral | Medium 3.5, Small 4 | Always include examples; every constraint explicit |
| Alibaba / Moonshot | Qwen3 / Kimi K2.6 | Structured markdown; multilingual; explicit schema |
| Other | Command R+, Phi-4, Unknown | RAG/citation framing; explicit schema fallback |

Full model rules → [`skill/SKILL.md`](skill/SKILL.md)

---

## More examples

Three complete before/after walkthroughs (GPT-5.5 · o3 · Mistral Medium 3.5) → [`examples/examples.md`](examples/examples.md)

---

## Contributing

PRs welcome — one concern per PR. See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md) for how to add a model or submit a new example.

---

## Author

**Alvaro Manzo** · [github.com/Alvaro-Manzo](https://github.com/Alvaro-Manzo)

---

## License

[MIT](LICENSE) © 2026 Alvaro Manzo
