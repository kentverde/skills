# PROJECT INTAKE SKILL

## Overview

A structured conversational framework for breaking down new projects into clear, outcome-driven plans. Replaces bottom-up task brainstorming with top-down goal-driven planning.

**Trigger phrase:** `Run Project Intake for [Project Name]`

**Core philosophy:** Every piece of work must trace back to a plainly stated goal. If you can't explain why a task exists in one sentence, it shouldn't be there.

---

## Naming Convention

All items use a hierarchical ID system:

| Level | Code | Example |
|---|---|---|
| Project | P# | P1 = Alta |
| Goal | G# | P1.G1 |
| Condition | C# | P1.G1.C1 |
| Task | T# | P1.G1.C1.T1 |
| Milestone | M# | P1.G1.C1.M1 (promoted from a task) |

Every item carries its full lineage. Reading the ID tells you exactly what it supports.

---

## Workflow

### PHASE 1 — Goals

**Ask:** "In plain English, what does success look like for this project?"

**Rules:**
- Allow up to 2-3 goals per project
- Apply a light nudge if language is vague, jargon-heavy, or abstract
- Each goal must pass the clarity test: "Could someone outside the company understand this, and would they know if you succeeded?"
- Suggest a clearer version if needed, but don't belabor it
- Confirm and lock each goal before proceeding

**Challenge patterns to watch for:**
- Deliverable-as-goal: "Develop a strategy" → push toward what the strategy achieves
- Jargon: "Increase market penetration" → what does that actually mean in plain terms?
- Unmeasurable: "Improve brand awareness" → how would you know?
- Process as a task: "Create a process" or "Define the process" → What is "being created" or what does "define" mean?

**Example exchange:**
```
User: "The goal is to develop a comprehensive merchandising plan."
Claude: "That sounds like a step toward a bigger outcome — what does the 
merchandising plan need to accomplish? Something like 'sell $X of product 
in the first 6 months' or 'get Alta placed in 200 retail locations'?"
```

---

### PHASE 2 — Conditions for Success

**Ask (for each goal):** "For that to happen, what needs to be true?"

**Rules:**
- No arbitrary limit on number of conditions — scale to the project
- Each condition must pass the must-have test: "If this weren't true, could the goal still happen?"
  - If YES → cut it or flag as nice-to-have (do not include in the plan)
  - If NO → it's a real condition, keep it
- Conditions are states, not actions ("Reps have samples" not "Ship samples")
- Each condition should be testable — you can look at it and say true or false
- Light nudge on vague language
- Watch for conditions that depend on decisions not yet made — flag as contingent with a decision gate
- Confirm and lock all conditions before proceeding

**Example conditions for "Sell $X of Alta in first 6 months":**
- Customers know the product exists
- Reps have samples in hand
- Pricing is finalized
- Inventory is available to ship

---

### PHASE 3 — Tasks

**Ask (for each condition):** "What do we actually need to do to make this true?"

**Rules:**
- Every task must be an action, not a deliverable
  - YES: "Decide pricing for the line"
  - NO: "Develop pricing strategy"
- Every task must have a clear finish line — you can tell when it's done
- Every task must directly trace back to a Condition for Success
  - Challenge any task that can't connect: "How does this help make [condition] true?"
  - If it can't be answered simply, reframe or remove
- Capture a due date for each task
- Flag dependencies: "This can't start until [X] is done"
- Do NOT assign ownership during intake — focus on the work itself
- Flag contingent tasks that depend on upstream decision gates

#### THE DELIVERABLE TEST (CRITICAL)

Every task must answer: **"What's the thing that exists when this is done?"**

If the answer isn't something tangible — a document, a spreadsheet, an SOP, a flowchart, a signed agreement, a configured system, a completed shipment — the task needs to be reframed.

**Do NOT accept tasks where the verb IS the deliverable.** The following words almost always signal a task that needs to be pushed further:

| Vague Language | Challenge With | Better Example |
|---|---|---|
| "Define X" | "What's the deliverable? A one-pager? An SOP? A spreadsheet?" | "Create a one-pager listing dealer requirements and benefits" |
| "Create a process" | "What format? SOP? Flowchart in Lucid/Visio?" | "Create an onboarding SOP with step-by-step flowchart (Lucid/Visio)" |
| "Evaluate / Assess" | "What decision does this produce? What document captures the answer?" | "Decide which channel options we can actually execute — resources, capabilities, partnerships" |
| "Address" | "What does done look like? A sign-off? A document? A decision?" | "Get legal review and written sign-off that our dealer model is compliant" |
| "Develop a strategy" | "What's the output? A plan with dates and owners?" | "Build a marketing campaign plan with specific deliverables, owners, and launch dates" |
| "Establish" | "What tangible thing exists when this is established?" | "Designate a named broadloom SME on the CS team as escalation point" |
| "Review" | "What's the output of the review? A list? A decision? A revised document?" | "Compile a list of at least 20 potential dealer partners in a shared file" |
| "Explore" | "What question are you trying to answer?" | "Determine if RepZio can support dealer requirements — done when we have a yes/no with documented gaps" |
| "Leverage" | "What are you actually using and how?" | "Configure RepZio with dealer accounts, customer assignments, and price levels" |
| "Strategize" | "What specific plan or decision is needed?" | "Decide how we'll price the dealer tier — done when margin structure is documented and approved" |

**When you encounter vague language:** Lightly challenge by asking what the tangible output is. Suggest a reframe. If the user confirms the reframe, lock it in. Do not belabor — one nudge is enough.

---

### PHASE 4 — Milestones & Waypoints

**Present:** "Each Condition for Success is automatically a milestone. Are there any tasks that should be elevated as key checkpoints for leadership? Are there any external waypoints we need to add?"

**If the user asks for help identifying milestones:** Walk through each condition and recommend which tasks are significant enough to report to leadership. Explain reasoning for each recommendation. Let the user approve, add, or remove.

**Rules:**
- All Conditions for Success are automatic milestones
- Any task can be promoted to a milestone by changing T → M in its ID
  - It stays in the same position in the hierarchy
- Custom waypoints can be added for cross-cutting events:
  - Go/no-go decisions
  - Launch dates
  - Board or leadership presentations
  - External deadlines (trade shows, customer commitments)
- Each milestone/waypoint gets a date
- Milestones appear inline in the visual tree with a ▶ marker

**Milestone selection criteria:**
- Decision gates that unlock other work streams
- External partnership agreements
- Moments where something becomes real (system goes live, team is certified, network is operational)
- Public-facing events (website launch, market announcement)
- Legal or compliance sign-offs

---

## Output Format

Generate a downloadable markdown file (.md) using the Visual Tree format.

### Template:

```
# Project Intake: [Project Name]
# Date: [Date]
# Project ID: P[#]

P[#]: [Project Name]

├── P[#].G1: [Goal in plain English]
│   ├── P[#].G1.C1: [Condition for Success]
│   │   ├── P[#].G1.C1.T1: [Task description] ([Due date])
│   │   ├── P[#].G1.C1.T2: [Task description] ([Due date])
│   │   │   └── Depends on: P[#].G1.C1.T1
│   │   └── ▶ P[#].G1.C1.M1: [Milestone description] ([Due date])
│   │       └── Depends on: P[#].G1.C1.T2
│   │
│   ├── P[#].G1.C2: [Condition for Success]
│   │   ├── P[#].G1.C2.T1: [Task description] ([Due date])
│   │   └── P[#].G1.C2.T2: [Task description] ([Due date])
│   │
│   └── ▶ P[#].G1.W1: [Custom waypoint — e.g., Go/No-Go Decision] ([Due date])
│       └── Depends on: P[#].G1.C1, P[#].G1.C2
│
├── P[#].G2: [Goal in plain English]
│   ├── ...
│   └── ...
```

### Additional output sections:

**Milestone Summary Table** — A quick-reference table listing all milestones with IDs, descriptions, target dates, and status.

**Key Decisions Made** — Document all decisions locked in during intake for future reference.

**Critical Path** — Identify decision gates and what they unlock. List work that can proceed now vs. what is blocked.

### Output rules:
- Every task shows its due date in parentheses (or TBD if unknown)
- Dependencies appear as indented notes below the item
- Milestones are marked with ▶
- Contingent items are marked with ⚠️ and note what they depend on
- Conditions for Success are inherently milestones (completion of all tasks beneath them)
- The tree reads top-down: Project → Goals → Conditions → Tasks/Milestones

---

## Conversation Flow Summary

1. **"Run Project Intake for [X]"** → Start
2. **Phase 1:** Ask for goals (2-3 max). Light nudge on clarity. Lock in.
3. **Phase 2:** For each goal, ask what must be true. Must-have test. Flag decision gates and contingencies. Lock in.
4. **Phase 3:** For each condition, ask what needs to be done. Action-oriented, dated, dependencies flagged. **Apply the Deliverable Test to every task — push back on vague verbs.** Lock in.
5. **Phase 4:** Review milestones. Promote tasks, add waypoints. Offer to walk through conditions and recommend milestones if user wants help. Lock in.
6. **Output:** Generate and deliver the visual tree as a downloadable markdown file with milestone summary, key decisions, and critical path.
