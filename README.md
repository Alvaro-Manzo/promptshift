# promptshift

[![MIT](https://img.shields.io/badge/license-MIT-blue.svg)]() [![Active](https://img.shields.io/badge/status-active-brightgreen.svg)]()  
Made for Claude Skills — model-aware prompt adaptation and repair.

Short summary

- Convert a generic prompt into a model-optimized prompt.  
- Produce a concise before/after with an explanation of changes and a numeric score.  
- Designed for prompt engineers and teams working across multiple LLMs.

Quickstart — pick one

- Web (no install, recommended): Create a new repository on GitHub `Alvaro-Manzo/promptshift`, then use **Add file → Upload files** to upload this repo's files. Commit directly to `main` with message `chore: standardize author to Alvaro-Manzo`.
- Local (if `git` is already available): run

```bash
git init
git add -A
git commit -m "chore: standardize author to Alvaro-Manzo"
git branch -M main
git remote add origin https://github.com/Alvaro-Manzo/promptshift.git
git push -u origin main
```

How to use the skill (summary)

- Import `skill/SKILL.md` into the Claude Skills UI or your Claude SDK as a skill.  
- Trigger with one of the phrases in the skill frontmatter (for example: "adapt for [model]" or "optimize this prompt").  
- The skill will run a triage + pattern-detection + model-adaptation + repair pass and return the enforced output format.

Minimal usage example (copy-paste ready)

Input: "Summarize the attached article about recent climate policy developments and their implications for global emissions."  
Target: Gemini 2.5 Pro

## ANALYSIS
The prompt is zero-shot and lacks audience, length, and output structure — pattern: zero-shot / summarization. Complexity: SIMPLE.

## OPTIMIZED PROMPT
Act as an expert policy analyst. Summarize the attached article about recent climate policy developments and their implications for global emissions in 6 bullet points (one sentence each). Include one short (2-sentence) takeaway for policymakers and one quantified key risk or uncertainty. Use imperative bullet labels and keep the total length under 200 words.

## CHANGES

- Added role: `expert policy analyst` → clarifies voice and framing for Gemini 2.5 Pro.  
- Converted zero-shot to structured brief → bullet list + exact counts to reduce ambiguity.  
- Added length constraint and policy-focused takeaway → reduces verbosity and increases actionability.

## SCORE
Before: 4/10  
After: 9/10  
Key gain: Precision and explicit structure reduce variance and improve factual, actionable output.

Supported models (condensed)

| Family | Example models | Prompt style |
|---|---|---|
| OpenAI | GPT-5.5, GPT-5.4, o3, GPT-4o | Role + explicit limits; anchor key instructions at end |
| Anthropic | Claude Opus / Sonnet | XML tags, explain WHY; CoT when useful |
| Google | Gemini 2.5 Pro / Flash | Bullet/imperative; explicit length constraints |
| xAI | Grok | Conversational framing; real-time/web context |
| DeepSeek | DeepSeek R1 / V4 | Explicit reasoning; format for math/code |
| Meta | Llama 4 / 3.3 | Few-shot preferred; short system prompts |
| Mistral | Medium 3.5, Small 4 | Few-shot examples; explicit schema |
| Alibaba / Moonshot | Qwen3 / Kimi | Structured markdown; multilingual support |
| Other | Command R+, Phi-4, Unknown | RAG/citation framing; explicit schema fallback |

Where to find more

- Examples: `examples/examples.md`  
- Contribution guidelines: `.github/CONTRIBUTING.md`  
- Issue templates: `.github/ISSUE_TEMPLATE/`

Contributing

Brief: open a PR with one concern per PR. See `CONTRIBUTING.md` for details.

Author & license

Alvaro-Manzo · https://github.com/Alvaro-Manzo  
MIT
# promptshift
