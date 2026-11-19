# Where the house data lives

The plugin keeps three things: **the house profile** (what's in the house), **the task list** (recurring and seasonal maintenance), and **the log** (what was done, when). Store them in Notion when a Notion connector is available, otherwise in plain markdown files. Never store a street address, alarm codes, or account numbers; a city or region is enough for seasonal timing.

## Pick the backend

1. If Notion tools are available, search Notion for a page titled **House**. If it exists, use it. If it doesn't and the user is running setup, create it there.
2. If no Notion tools are available, or the user says they don't use Notion, use files in a `House/` folder in the working folder.
3. If both exist, prefer whichever the house profile says (`Storage:` line).

## Notion layout

A page titled **House** (icon 🏠). Put the two databases at the **top of the page, inline**, so opening the page shows the tasks straight away. The profile goes below them.

1. **House Tasks** database (inline, first on the page):
   | Property | Type | Notes |
   |---|---|---|
   | Task | title | e.g. "Replace furnace filter" |
   | System | select | Furnace, Water softener, AC, Plumbing, Exterior, Safety… |
   | Timing | text | "Every 3 months", "Fall: before first freeze", "Monthly" |
   | Last done | date | |
   | Next due | date | Blank for seasonal tasks until the season's window is set |
   | Lead time | text | What to do ahead: "buy a filter (16x25x1)" |
   | Notes | text | |
   | Status | status | Options in this order: **Later** (to-do group), **Next up** (to-do group), **In progress** (in-progress group), **Done** (complete group) |

   Set Status from Next due: due more than 30 days out → Later; due within 30 days or overdue → Next up. The user drags cards to In progress and Done themselves.

   Create three views, in this order:
   - **Up next** (table): sorted by Next due, ascending. Make it the first view.
   - **Calendar** (calendar): by Next due, showing Task and System.
   - **Board** (board): a classic kanban grouped by Status, columns left to right Later → Next up → In progress → Done, showing empty columns, sorted by Next due, showing Task, Next due and System.
2. **Home Log** database (inline, second): one view, **Newest first** (table, sorted by Date descending).
   | Property | Type | Notes |
   |---|---|---|
   | Entry | title | Short: "Added salt", "Furnace serviced" |
   | Date | date | |
   | System | select | Same options as House Tasks |
   | Who | select | Me / Pro |
   | Cost | number | Optional |
   | Notes | text | Findings, company name, warranty, follow-ups |
3. **Profile** section (heading, below the databases): city/region, home type, heating, cooling, water source, a bulleted list of systems (with brand/model when known), and the name of the user's to-do list if they have one.

**Don't link or embed the user's own to-do list on the House page.** No mention, no linked view: write its name as plain text in the profile only. A link there sits above the house data and takes people to the wrong list.

If the tools can't create a view type, create the rest and tell the user which view to add by hand (one click in Notion: "+ Add view").

## File layout

```
House/
├── house.md   # profile, same fields as the Notion profile section, plus "Storage: files"
├── tasks.md   # one markdown table with the House Tasks columns
└── log.md     # newest first: "## YYYY-MM-DD — System" then What / Who / Cost / Notes bullets
```

## Rules for both

- When something is logged that matches a task, set that task's Last done and recalculate Next due.
- Tasks recur, so a Done card doesn't stay done. When a task is logged, or found in Done during a check-in, set Last done (today, or the date the user gives), recalculate Next due, add a Home Log entry if there isn't one, and move it back to Later or Next up using the 30-day rule.
- On every check-in, move Later cards whose Next due is now within 30 days to Next up. Leave In progress cards alone.
- Dates are ISO (YYYY-MM-DD). Compute "how long ago" from today's date.
- Keep entries short and factual. Don't invent details the user didn't give.
