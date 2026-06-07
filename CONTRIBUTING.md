# Contributing to promptshift

Thank you for your interest in improving promptshift. We welcome contributions that expand model coverage, add examples, improve existing guidance for any supported model.

How to propose a new model

- Provide: model name and version.
- Document confirmed anti-patterns observed in practice.
- Provide confirmed optimizations (concise list of rules).
- Include evidence: links to docs, tests, or reproducible example prompts and outputs.

How to submit a new example

- Follow the format used in `examples/examples.md` (ANALYSIS, OPTIMIZED PROMPT, CHANGES, SCORE).
- Keep examples focused and reproducible.

PR guidelines

- Use a clear title: "Add model: <Model Name>" or "Add example: <short description>".
- One concern per PR; keep changes small and reviewable.
- In the PR description, explain what changed and why, include at least one example demonstrating the improvement, and include a commit example using a conventional prefix such as:
-  `feat: add model`
-  `fix: x`
-  `docs: update README`
-  `chore: something`
-  `refactor: simplify logic`
-  `test: add coverage`.
