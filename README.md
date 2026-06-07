# promptshift

[![MIT](https://img.shields.io/badge/license-MIT-blue.svg)]() [![Active](https://img.shields.io/badge/status-active-brightgreen.svg)]()  
Made for Claude Skills

promptshift adapts and optimizes prompts for specific AI models. Given a prompt and a target model, it applies model-aware transformation rules, repairs structural issues, and returns a scored before/after result.

## What it solves

- Prompts that fail silently because they are generic and not tailored to a model's strengths.
- Variance in output quality across models due to missing role, format, or examples.

## How it works

- Triage the incoming prompt (simple vs complex).
- Detect prompt pattern (zero-shot, few-shot, CoT, role-based, etc.).
- Classify the task (reasoning, coding, writing, extraction, summarization, planning, RAG, agent, multimodal).
- Apply model-specific rules from a built knowledge base to adapt wording, structure, and examples.
- Run a repair pass and produce a structured before/after with a score.

## Supported models

| Family | Models | Prompt style |
|---|---|---|
| OpenAI | GPT-5.5, GPT-5.4, o3, GPT-4o | Role + explicit limits; anchor key instructions at end |
| Anthropic | Claude Opus 4.8 / 4.7, Claude Sonnet 4.6 | XML tags, explain WHY; allow CoT when useful |
| Google | Gemini 2.5 Pro, Gemini 2.5 Flash | Bullet/imperative, explicit length constraints |
| xAI | Grok 4.3, Grok 4.1 | Conversational framing; tolerate less rigid structure; real-time/web context framing |
| DeepSeek | DeepSeek R1, DeepSeek V4 Pro/Flash | Explicit reasoning framing; explicit format for code and math |
| Meta | Llama 4 Scout, Maverick, Llama 3.3 | Few-shot preferred; short system prompts; explicit schema; vision-aware where relevant |
| Mistral | Mistral Medium 3.5, Mistral Small 4 | Always include examples; explicit constraints; concise responses |
| Alibaba / Moonshot | Qwen3, Qwen 3.6, Kimi K2.6 | Explicit schemas; structured markdown; multilingual and long-context strengths |
| Other | Command R+, Phi-4, Gemma 3, Unknown | RAG/citation framing; single-task, explicit format; universal fallback: role + example + explicit format |

## Installation

1. Copy `skill/SKILL.md` into Claude Skills import UI or follow Claude SDK instructions for skill registration.
2. Ensure the skill is enabled for the agent and that triggers include the listed trigger phrases.
3. Optionally, add `examples/examples.md` to your repository for team reference.

## Usage (worked example)

Input: "Summarize the attached article about recent climate policy developments and their implications for global emissions."  
Target: Gemini 2.5 Pro

## ANALYSIS
The prompt is zero-shot, vague on audience and angle, and lacks length constraints — pattern: zero-shot / summarization. Complexity: SIMPLE.

## OPTIMIZED PROMPT
Act as an expert policy analyst. Summarize the attached article about recent climate policy developments and their implications for global emissions in 6 bullet points: 1 sentence each. Include one short (2-sentence) takeaway for policymakers and one quantified risk or uncertainty. Use clear, imperative bullet labels and keep total length under 200 words.

## CHANGES

[Added role: "expert policy analyst"] → Gemini 2.5 Pro responds best to imperative role framing and structured output.
[Converted zero-shot to structured brief] → Bullet format + explicit counts reduces ambiguity.
[Added length limit and exact items] → Prevents verbosity and aligns with Gemini token preferences.
[Added policy-focused takeaway and quantified risk] → Matches Gemini's strength for focused analytical output.

## SCORE
Before: 4/10  
After: 9/10  
Key gain: Precision and explicit structure reduce variance and improve factual, actionable output.

## More examples

See `examples/examples.md` for additional before/after adaptations.

## Contributing

Contributions welcome — see `.github/CONTRIBUTING.md` for guidelines.

## Author

Alvaro-Manzo · https://github.com/Alvaro-Manzo

## License

MIT
# promptshift
