## R1

Original Prompt:
Create a 30-day study plan for learning Python.


PromptShift Output:

Act as a Python curriculum designer. Create a 30-day study plan for a complete beginner with no prior programming experience who can commit 1 hour per day.
Learning goal: Be able to build and deploy a simple data dashboard using Python by day 30.
Plan structure (follow exactly):

Organize into 4 weekly phases:

Week 1 — Python fundamentals (syntax, variables, loops, functions)
Week 2 — Intermediate concepts (OOP, file I/O, error handling, modules)
Week 3 — Data libraries (Pandas, NumPy, Matplotlib basics)
Week 4 — Project week (build and deploy a simple data dashboard)



For each day include:

Day number and topic title
One primary learning objective (1 sentence)
One concrete exercise or mini-project (1 sentence)
Estimated time: 60 minutes

Resource constraints:

Free resources only (docs.python.org, freeCodeCamp, Kaggle Learn, YouTube)
No paid courses or books

Output format:

Markdown table for each week (columns: Day, Topic, Objective, Exercise)
One short paragraph per week summarizing the phase goal
Closing section: 3 tips for staying on track during the 30 days
No explanation or meta-commentary outside the plan itself

Constraints:

Each objective must be measurable (avoid "understand X"; prefer "write a function that does X")
Each exercise must be completable in under 30 minutes
No repeated topics across days

Intent Preserved:
[1]

Requirement Invention:
[Major]

Model choosen:
[Gemini-3.0]

## R2 

Original Prompt:

Compare React and Vue for a startup.


PromptShift Output:
Act as a senior software architect advising an early-stage startup. Compare React and Vue across the dimensions below and deliver a final recommendation.
Startup context:

Team size: 3 frontend developers (2 junior, 1 mid-level)
Product: B2B SaaS dashboard (data-heavy, moderate UI complexity)
Timeline: MVP in 12 weeks
Budget: Bootstrapped — no paid tooling
Existing stack: Node.js backend, no frontend framework yet

Evaluate across these dimensions:
DimensionWhat to assessLearning curveTime to productive output for junior devsEcosystem & librariesAvailability of free, maintained UI and charting libsHiring & talent poolRelative market availability of experienced devsPerformanceRendering efficiency for data-heavy dashboardsLong-term maintainabilityCommunity health, release cadence, breaking change riskStartup fitSpeed of initial setup, boilerplate, and DX
Output format:

One paragraph per dimension (4–6 sentences each)
A scored comparison table (React vs Vue, 1–5 per dimension, with one-line justification)
A final recommendation section (3–5 sentences) — must pick one and justify the choice given this specific context
No hedging conclusions (e.g. "it depends on your needs") — commit to a recommendation

Constraints:

Base claims on current ecosystem state (2024–2025)
Flag any dimension where the gap between React and Vue is negligible
No mention of Angular, Svelte, or other frameworks unless directly relevant to the recommendation

Intent Preserved:
[0]

Requirement Invention:
[Major]

Model choosen:
[ChatGPT-5.0]