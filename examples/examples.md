# Examples — promptshift

Three worked examples demonstrating before/after adaptations.

---

## Example 1 — Vague writing prompt → GPT-5.5

Input:
"Write a short piece about the benefits of remote work."

Target: GPT-5.5

ANALYSIS
Pattern: zero-shot / writing; issues: no audience, no tone, no length, generic ask. Complexity: SIMPLE.

OPTIMIZED PROMPT
You are a persuasive communications specialist. Write a 3-paragraph piece (each paragraph 2-3 sentences) describing the benefits of remote work for mid-level managers considering hybrid policies. Use a professional, optimistic tone, include one short example of increased productivity, and end with a one-sentence recommendation for policy. Total length: ~140-180 words.

CHANGES

[Added role: "persuasive communications specialist"] → GPT-5.5 performs better with explicit role framing.
[Specified audience: "mid-level managers"] → Focuses examples and tone.
[Added structure: 3 paragraphs] → Controls output shape and length.
[Added recommendation requirement] → Increases actionability.

SCORE
Before: 3/10
After: 9/10
Key gain: Clear audience and structure produce targeted, ready-to-use copy.

---

## Example 2 — CoT prompt incorrectly applied → o3

Input:
"Think step by step and solve: Prove that the sum of the first n integers is n(n+1)/2."

Target: o3

ANALYSIS
Pattern: explicit CoT instruction used. Anti-pattern for o3: "think step by step" causes verbosity and can degrade concise proofs. Complexity: SIMPLE (mathematical proof).

OPTIMIZED PROMPT
Provide a concise mathematical proof that the sum of the first n positive integers equals n(n+1)/2. Present a short proof (3–6 lines) using induction or pairing argument, then give a one-sentence intuition. Prefer clear equations and minimal prose.

CHANGES

[Removed explicit "think step by step"] → o3 prefers concise, direct proofs without CoT scaffolding.
[Added allowed methods: "induction or pairing argument"] → Guides the proof style and reduces hallucinated approaches.
[Requested short proof and one-sentence intuition] → Balances rigor and readability for o3's strengths.

SCORE
Before: 5/10
After: 9/10
Key gain: Removes CoT anti-pattern and yields a focused, concise mathematical answer.

---

## Example 3 — Zero-shot extraction → Mistral Medium 3.5

Input:
"Extract name, email, and company from this resume text: [resume text]."

Target: Mistral Medium 3.5

ANALYSIS
Pattern: zero-shot extraction. Issue: missing examples and schema; Mistral Medium benefits from explicit examples and strict output format. Complexity: SIMPLE.

OPTIMIZED PROMPT
You are an information extraction engine. Extract the following fields from the provided resume text and return valid JSON with keys `name`, `email`, and `company`. If a field is missing, set its value to null. Example outputs (few-shot):

Example 1 Input: "John Doe\nSenior Engineer\njohn.doe@example.com\nAcme Corp"
Example 1 Output: {"name":"John Doe","email":"john.doe@example.com","company":"Acme Corp"}

Example 2 Input: "Jane Smith — Data Scientist — jane@data.co — OpenAI"
Example 2 Output: {"name":"Jane Smith","email":"jane@data.co","company":"OpenAI"}

Now extract from: [resume text]

CHANGES

[Converted zero-shot to few-shot] → Adds two concrete examples to guide Mistral's pattern matching.
[Enforced JSON schema and null defaults] → Prevents format drift and missing-field ambiguity.
[Specified role as extraction engine] → Aligns expectations for structured output.

SCORE
Before: 4/10
After: 9/10
Key gain: Few-shot examples and explicit schema significantly increase precision and JSON compliance.
