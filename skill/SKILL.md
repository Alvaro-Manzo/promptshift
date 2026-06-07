---
name: promptshift
description: |
  Model-aware prompt adapter for Claude. Trigger phrases: "optimize this prompt", "adapt for [model]", "rewrite for [model]", "this prompt is for [model]", "make this work on [model]", "prompt isn't performing on [model]", "translate prompt to [model]". Use aggressively when model-specific adaptation or optimization is required.
---

**Triage — first step always:**

- SIMPLE: single task, clear intent, one output type → skip to model adaptation
- COMPLEX: multi-step, agentic, contradictions, high-stakes → run full workflow

**Full workflow:**

1. Triage (simple / complex)
2. Pattern detection: zero-shot / few-shot / role-based / CoT / ReAct / tool-calling / RAG / hybrid
3. Task classification (multi-label): reasoning / coding / writing / extraction / summarization / planning / RAG / agent / multimodal / other
4. Model adaptation using knowledge base
5. Repair pass: ambiguities → explicit; weak constraints → add schema; contradictions → resolve; redundancy → cut; missing examples when needed → add one
6. Structured output

**Model knowledge base — render as markdown table: Model | Anti-patterns to avoid | Key optimization rules**

Group by family:

**OpenAI**

| Model | Anti-patterns to avoid | Key rules |
|---|---|---|
| GPT-5.5 | Over-scaffolding, no role | Assign explicit role; Objective + Context formula; constrain output length; anchor instructions at end; strong at reasoning and code |
| GPT-5.4 / GPT-5.4 Thinking | Explicit CoT on Thinking variant | For Thinking variant treat like o1 (no CoT); for base variant use explicit role + format |
| o3 / o4-mini | Explicit chain-of-thought | No "think step by step"; state goal only; trust internal reasoning; minimal scaffolding |
| GPT-4o | Verbosity without constraints | Role + goal + explicit length limit; anchor key instructions at end |

**Anthropic**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Claude Opus 4.8 / 4.7 | Over-constraining, contradictions | XML tags for structure; explain WHY not just WHAT; "think step by step" works well; audit for contradictions; extended thinking opt-in for hard tasks |
| Claude Sonnet 4.6 | Loose output format | XML tags; explicit format; strong at code and long documents |

**Google**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Gemini 2.5 Pro | Abstract prose instructions | Bullet-point instructions; imperative verbs; explicit length constraints; "Analyze this file" framing for multimodal |
| Gemini 2.5 Flash | Ambiguous brevity | Specify exact word/token targets; optimizes aggressively for speed |

**xAI**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Grok 4.3 / 4.1 | Overly formal prompts | Conversational framing; real-time web context works natively; "Investigate and summarize" framing; tolerates less structure |

**DeepSeek**

| Model | Anti-patterns | Key rules |
|---|---|---|
| DeepSeek R1 | Explicit reasoning instructions | Treat like o1; "reason in detail" framing works; no step-by-step scaffolding; strong on math and logic |
| DeepSeek V4 Pro / Flash | Loose output constraints | Explicit format; role assignment helps; 1M context; strong agentic coding; "Generate complete code" framing |

**Meta**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Llama 4 Scout / Maverick | Abstract rules, long system prompts | Few-shot over zero-shot; "Act as expert" role framing; explicit output format; keep system prompt under 300 tokens; leverage vision natively |
| Llama 3.3 | Same as above | Few-shot; short system prompt; explicit schema |

**Mistral**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Mistral Medium 3.5 | Abstract or implicit constraints | Always include examples; every constraint explicit; 128B dense model — consistent and predictable; "Concise response" framing; open-weight |
| Mistral Small 4 | Complex multi-step | Single task per prompt; explicit format; fine-tunable |

**Alibaba / Moonshot**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Qwen3 / Qwen 3.6 | Unformatted prompts | Explicit schemas; structured markdown; strong multilingual and code; "Explain with examples" framing |
| Kimi K2.6 | Implicit context | State all context explicitly; strong for long-horizon research and agentic coding; "Research deeply" framing |

**Other**

| Model | Anti-patterns | Key rules |
|---|---|---|
| Command R+ | Ignoring RAG strengths | Citation instructions; explicit source referencing; grounded generation framing |
| Phi-4 / Gemma 3 | Multi-step complexity | Single task per prompt; explicit format required |
| Unknown model | — | Universal version: clear role + explicit format + one example + no CoT assumption |

**Enforced output format — Claude must always return exactly this:**

ANALYSIS
[2-3 sentences: pattern identified, main issues, complexity level]
OPTIMIZED PROMPT
[Complete prompt, ready to copy-paste]
CHANGES

[Change] → [Model-specific reason from knowledge base]
(list all changes)

SCORE
Before: X/10
After:  X/10
Key gain: [one line]


**Worked example**

- Input: "Summarize the attached article about recent climate policy developments and their implications for global emissions." (vague; no audience, length, or angle)
- Target: Gemini 2.5 Pro

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

Constraints: under 400 lines; return only the enforced output format for each adaptation.
