## U1 

Original Prompt:
Find and fix the bug in this JavaScript function.

PromptShift Output:
Build a freelancer dashboard as a single self-contained HTML file using HTML, CSS, and vanilla JavaScript.
Display these three sections:

Revenue — total earned this month, with a simple bar chart by week
Expenses — total spent this month, itemized by category
Active Clients — list of current clients with name, project, and status badge

Use this hardcoded sample data:
jsconst data = {
  revenue: { total: 8400, weekly: [1200, 2100, 3300, 1800] },
  expenses: { total: 1950, categories: { tools: 300, hosting: 150, contractors: 1500 } },
  clients: [
    { name: "Acme Corp", project: "Website Redesign", status: "active" },
    { name: "Nova LLC", project: "API Integration", status: "review" },
    { name: "Orbit Co", project: "Mobile App", status: "active" }
  ]
};
Requirements:

Clean, minimal UI with a dark or light theme (your choice)
Responsive layout (works on desktop and mobile)
No external libraries or frameworks
All code in one file, ready to open in a browser

Output: one complete HTML file only. No explanation unless a decision needs justification.

Intent Preserved:
[1]

Requirement Invention:
[Major]

Model choosen:
[Grok]

## U2

Original Prompt:
Create a Kanban board with drag and drop.

PromptShift Output:
Build a fully functional Kanban board as a single React component using only React hooks and Tailwind CSS utility classes.
Column structure:

Todo
In Progress
Review
Done

Each card must display:

Task title
Priority badge (Low / Medium / High)
Assignee initials avatar

Use this hardcoded sample data:
jsconst initialCards = [
  { id: "1", title: "Design landing page", priority: "High", assignee: "AK", column: "Todo" },
  { id: "2", title: "Fix auth bug", priority: "High", assignee: "MR", column: "In Progress" },
  { id: "3", title: "Write API docs", priority: "Medium", assignee: "SL", column: "Review" },
  { id: "4", title: "Deploy staging build", priority: "Low", assignee: "AK", column: "Done" },
  { id: "5", title: "Set up CI pipeline", priority: "Medium", assignee: "MR", column: "Todo" }
];
Drag and drop requirements:

Use the native HTML5 Drag and Drop API only — no external DnD libraries
Cards must be draggable between columns
Highlight the target column on dragover
Persist card order within columns after drop

UI requirements:

Clean minimal layout with visible column headers and card counts
Priority badge color-coded: High = red, Medium = yellow, Low = green
Smooth visual feedback on drag (opacity change on dragged card)
Fully responsive layout

Output format:

One .jsx file with a default export
No explanation unless a design decision needs justification
All state managed with useState only — no external state libraries

Intent Preserved:
[1]

Requirement Invention:
[Major]

Model choosen:
[Claude-Sonnet-4.6]
