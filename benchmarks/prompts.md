Si tu objetivo es demostrar que PromptShift funciona, no necesitas 500 prompts. Necesitas unos **30-50 prompts cuidadosamente elegidos** que representen problemas reales.

# Estructura del benchmark

```text
benchmarks/
├── coding.md
├── ui-ux.md
├── writing.md
├── reasoning.md
├── rag.md
└── evaluation.md
```

---

# Métricas

## 1. Intent Preservation

Pregunta:

> ¿La tarea sigue siendo exactamente la misma?

Escala:

```text
2 = Intent preserved
1 = Minor drift
0 = Task changed
```

---

## 2. Prompt Expansion Ratio

```text
optimized_tokens / original_tokens
```

Ejemplo:

```text
40 → 50 = 1.25x
40 → 200 = 5x
```

Para PromptShift, cuanto menor mejor.

---

## 3. Human Quality Rating

```text
Better
Same
Worse
```

---

## 4. Requirement Invention

```text
Yes
No
```

¿Añadió requisitos que el usuario nunca pidió?

---

# Coding Benchmark

## C1 Refactor

```text
Refactor this Python function without changing behavior.
```

---

## C2 Bug Fix

```text
Find and fix the bug in this JavaScript function.
```

---

## C3 SQL

```text
Optimize this SQL query for performance.
```

---

## C4 React

```text
Create a React component for a login form.
```

---

## C5 API

```text
Write a REST API endpoint that creates a user.
```

---

## C6 Unit Tests

```text
Generate unit tests for this function.
```

---

## C7 TypeScript

```text
Convert this JavaScript file to TypeScript.
```

---

## C8 Refactoring

```text
Simplify this code while preserving functionality.
```

---

## C9 Debugging

```text
Explain why this code throws an exception.
```

---

## C10 Documentation

```text
Generate documentation for this API.
```

---

# UI/UX Benchmark

## U1 Dashboard

```text
Create a freelancer dashboard showing revenue, expenses, and active clients.
```

---

## U2 Kanban

```text
Create a Kanban board with drag and drop.
```

---

## U3 Mortgage Calculator

```text
Build a mortgage calculator with sliders.
```

---

## U4 Flashcards

```text
Build a flashcard app for language learning.
```

---

## U5 Recipe App

```text
Create an app for storing and searching recipes.
```

---

## U6 Hero Section

```text
Design a hero section for an AI website.
```

---

## U7 Pricing Cards

```text
Create three pricing cards using glassmorphism.
```

---

## U8 SaaS Signup

```text
Build a multi-step registration form.
```

---

## U9 FAQ Accordion

```text
Create an animated FAQ accordion.
```

---

## U10 Admin Sidebar

```text
Design a collapsible admin sidebar.
```

---

# Writing Benchmark

## W1 Blog

```text
Write a blog post about remote work.
```

---

## W2 Email

```text
Write a professional follow-up email.
```

---

## W3 Summary

```text
Summarize this article.
```

---

## W4 LinkedIn

```text
Write a LinkedIn post announcing a product launch.
```

---

## W5 Product Description

```text
Write a product description for a smartwatch.
```

---

## W6 Newsletter

```text
Create a weekly newsletter.
```

---

## W7 Press Release

```text
Write a press release.
```

---

## W8 YouTube Script

```text
Create a YouTube video script.
```

---

## W9 Landing Page Copy

```text
Write landing page copy.
```

---

## W10 Case Study

```text
Write a customer success case study.
```

---

# Reasoning Benchmark

## R1 Planning

```text
Create a 30-day study plan for learning Python.
```

---

## R2 Decision Making

```text
Compare React and Vue for a startup.
```

---

## R3 Tradeoffs

```text
Evaluate the pros and cons of microservices.
```

---

## R4 Prioritization

```text
Prioritize these product features.
```

---

## R5 Root Cause

```text
Analyze why this project failed.
```

---

## R6 Architecture

```text
Design a scalable notification system.
```

---

## R7 Estimation

```text
Estimate the cost of building a SaaS MVP.
```

---

## R8 Strategy

```text
Create a GTM strategy for a new AI product.
```

---

## R9 Hiring

```text
Design an interview process for software engineers.
```

---

## R10 Risk Analysis

```text
Identify risks in this migration plan.
```

---

# RAG Benchmark

## G1

```text
Answer using only the provided documents.
```

---

## G2

```text
Summarize these PDFs and cite sources.
```

---

## G3

```text
Extract contract obligations from the attached files.
```

---

## G4

```text
Create a report based on these documents.
```

---

## G5

```text
Answer customer questions using the knowledge base.
```

---


