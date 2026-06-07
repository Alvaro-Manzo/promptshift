# PromptShift

[![MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Active](https://img.shields.io/badge/status-active-brightgreen.svg)](https://github.com/Alvaro-Manzo/promptshift)
[![Made for Claude Skills](https://img.shields.io/badge/made%20for-Claude%20Skills-blueviolet.svg)](skill/SKILL.md)

PromptShift is a model-aware prompt adapter for Claude.

Unlike most prompt optimizers, PromptShift follows a conservative approach:

> Clarify first. Preserve intent. Adapt to the model only when it matters.

Its goal is not to make prompts longer. Its goal is to make them clearer, more reliable, and easier for different model families to execute consistently.

---

## Why PromptShift Exists

Many prompt optimization tools introduce new requirements, audiences, or constraints that were never part of the original request.

For example:

**Original prompt**

```text
Summarize this article.
```

**Typical optimizer**

```text
Act as an expert policy analyst.
Summarize the article for decision-makers.
Include risks, opportunities, and strategic recommendations.
```

The task has changed.

PromptShift treats this as a failure.

The objective is to improve prompt quality without changing the user's intent.

---

## Design Principles

PromptShift follows five principles:

1. **Clarity first**

   * Remove ambiguity before adding structure.

2. **Preserve intent**

   * Do not invent goals, audiences, constraints, or evaluation criteria.

3. **Minimal change**

   * If the prompt is already good, leave it alone.

4. **Model adaptation second**

   * Apply model-specific guidance only when it materially improves the rewrite.

5. **Evidence over folklore**

   * Prefer broadly supported prompting practices over model-specific myths.

---

## What It Does

PromptShift can:

* Clarify ambiguous instructions.
* Normalize prompt structure.
* Remove contradictions.
* Reduce redundancy.
* Add output schemas when needed.
* Adapt prompts across model families.
* Preserve original intent.

PromptShift intentionally avoids:

* Prompt bloat.
* Artificial complexity.
* Role inflation.
* Requirement invention.
* Unsupported optimization tricks.

---

## Workflow

```text
Input Prompt
      │
      ▼
   Triage
      │
      ▼
 Clarify Intent
      │
      ▼
 Repair Issues
      │
      ▼
 Minimal Model Adaptation
      │
      ▼
 Optimized Prompt
```

---

## Example

### Input

```text
Summarize the attached article about recent climate policy developments and their implications for global emissions.
```

### Output

```text
## ANALYSIS

The prompt is underspecified because it does not define output shape or length. The task itself is clear.

## OPTIMIZED PROMPT

Summarize the attached article about recent climate policy developments and their implications for global emissions.

Output requirements:
- 6 bullet points
- One sentence per bullet
- Maximum 200 words

## CHANGES

Added explicit output structure.
Added length constraint.

## CONFIDENCE

High
```

Notice that the objective remains unchanged.

PromptShift improves clarity without redefining the task.

---

## Supported Adaptation Profiles

| Profile            | Typical Use Case              |
| ------------------ | ----------------------------- |
| Unknown / Mixed    | Safe default behavior         |
| Reasoning-Oriented | Logic, planning, analysis     |
| Format-Sensitive   | Structured outputs, schemas   |
| Retrieval-Oriented | Source-grounded tasks         |
| Conversational     | Natural-language interactions |

The skill includes model-family mappings for Claude, GPT, Gemini, Grok, DeepSeek, Llama, Mistral, Qwen, Kimi, and Command R+.

---

## Non-Goals

PromptShift does not:

* Guarantee better outputs.
* Replace prompt iteration.
* Add missing business requirements.
* Inject domain expertise automatically.
* Depend on hidden chain-of-thought.
* Optimize for benchmark scores.

---

## Installation

```bash
git clone https://github.com/Alvaro-Manzo/promptshift.git
```

Copy `skill/SKILL.md` into your Claude Skills directory and enable the skill.

---

## Contributing

Contributions are welcome.

When proposing a new adaptation rule:

* Explain why it helps.
* Provide evidence or repeatable observations.
* Prefer general principles over model-specific quirks.

---

## License

MIT License © 2026 Alvaro Manzo
