---
name: home-log
description: This skill should be used when the user wants to record something done to their home or look up its history, or says things like "log that I added salt", "the plumber came today", "I replaced the furnace filter", "when did I last…", "how much have I spent on the house", or "what work has been done".
---

# Home Log

Keep a running history of what was done to the house: maintenance, repairs, service visits, purchases, and problems. It answers "when did I last…?", helps when talking to a contractor, and is useful when selling the home.

Read `${CLAUDE_PLUGIN_ROOT}/references/storage.md` for where the log lives.

## Logging

1. Get the date (default today), the system, what was done, and who did it. Don't ask for anything the user's message already says.
2. For pro visits, also ask for the company, cost, any warranty on the work, and anything they recommended. Don't push for details the user doesn't have.
3. Keep entries short and factual.
4. If the entry matches a task, update that task's Last done and Next due, and move its card back to Later or Next up (30-day rule in storage.md).
5. If a pro recommended future work ("replace the anode rod within a year"), offer to add it as a task.
6. Confirm in one line: "Logged: added salt to the softener, today. Next check Dec 15."

## Looking things up

- "When did I last…": search the log and answer with the date and how long ago.
- Spending: total the cost fields for the period asked, broken down by system.
- Contractor prep: summarise one system's history in a few lines the user can read to the technician.
