---
name: promptshift
description: |
  Model-aware prompt adapter for Claude. Trigger phrases: "optimize this prompt", "adapt for [model]", "rewrite for [model]", "this prompt is for [model]", "make this work on [model]", "prompt isn't performing on [model]", "translate prompt to [model]". Use aggressively whenever prompt adaptation or model-specific optimization is involved.
---

**Purpose**

PromptShift rewrites prompts by removing ambiguity, preserving intent, and applying only the smallest useful adjustment.

**Core principles**

- Clarity first.
- Preserve intent.
- Minimal change.
- Model adaptation second.
- Prefer evidence over folklore.

**Triage — first step always**

- SIMPLE: one task, clear intent, one output type → rewrite directly
- COMPLEX: multi-step, contradictory, agentic, or high-stakes → decompose and rewrite

**Rewrite rules**

1. Preserve the original goal, audience, constraints, and evaluation criteria unless they are missing or contradictory.
2. Do not invent new requirements.
3. Do not expand the prompt unless the added text reduces ambiguity, improves reliability, enforces required format, or prevents a likely failure mode.
4. If the prompt is already clear, structured, and constrained, make only cosmetic fixes or return it unchanged.
5. Use model-specific adaptation only when it materially changes the rewrite.

**Repair pass**

- Make missing context explicit.
- Remove contradictions.
- Cut redundancy.
- Add only the minimum structure needed for reliable output.
- Avoid prompt bloat.

**Minimal model guidance**

- Unknown / mixed models: clear role, explicit format, one example only if needed, one length constraint only if needed.
- Reasoning-oriented models: keep instructions direct; avoid forcing visible chain-of-thought.
- Format-sensitive models: use concise schema, bullets, sections, or XML only when structure matters.
- Retrieval-oriented models: require citations and grounded source use.
- Conversational models: keep the prompt direct and task-focused.

**Evidence rule**

- Prefer rules with broad public support or repeated observation.
- Treat model-version claims as temporary heuristics.
- Label uncertain rules as heuristics, not facts.

**Output format**

Return exactly one of these:

### If changed
## ANALYSIS
[2-3 sentences: what was unclear, what was changed, why it was necessary]

## OPTIMIZED PROMPT
[rewritten prompt]

## CHANGES
[change] → [why it was necessary]

## CONFIDENCE
[Low / Medium / High]

### If unchanged
## ANALYSIS
[2-3 sentences: the prompt was already clear and required no substantive rewrite]

## OPTIMIZED PROMPT
[unchanged prompt]

## CHANGES
No substantive changes.

## CONFIDENCE
High

**Worked example**

- Input: "Summarize the attached article about recent climate policy developments and their implications for global emissions." (vague; no audience, length, or angle)
- Target: Gemini 2.5 Pro

## ANALYSIS
The prompt is underspecified: it lacks audience, angle, and output shape. Complexity: SIMPLE.

## OPTIMIZED PROMPT
Act as an expert policy analyst. Summarize the attached article about recent climate policy developments and their implications for global emissions in 6 bullet points, one sentence each. Include one short takeaway for policymakers and one quantified risk or uncertainty. Keep the total length under 200 words.

## CHANGES

[Added role: "expert policy analyst"] → Clarifies framing.
[Added exact structure] → Controls output shape.
[Added length limit] → Prevents verbosity.
[Added policy takeaway and risk] → Forces a more useful summary.

## CONFIDENCE
High

**Maintenance note**

Revalidate model guidance periodically. Remove any rule that no longer produces measurable benefit.
