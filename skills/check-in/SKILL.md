---
name: check-in
description: This skill should be used for the weekly house check-in, or when the user asks "what's coming up for the house", "what maintenance is due", "house check-in", "what should I do before winter", or "anything I need to do around the house this week". Also used when a scheduled task asks to run the house check-in.
---

# Weekly House Check-in

A short weekly conversation that keeps one busy person ahead of their house: what's coming up, what to prep, and a chance to mention anything that seems off. Calm and brief. Most weeks, very little is due; say so in a line and don't pad.

Read `${CLAUDE_PLUGIN_ROOT}/references/storage.md` and load the house profile, task list, and recent log. If there's no profile yet, offer to run setup first (setup skill).

## 1. Work out what matters this week

First, tidy the board (Notion only; see storage.md): log and reset anything the user moved to **Done** since the last check-in, and move **Later** cards due within 30 days to **Next up**. Mention what you logged in one line ("Saw you finished the gutters, logged it.").

Using today's date:

- **Overdue:** Next due before today.
- **Coming up:** Next due in the next 14 days.
- **Prep needed:** tasks due in the next 21 days whose Lead time involves buying something or booking someone. Flag these early: "Furnace filter is due on the 28th. Grab a 16x25x1 this week."
- **Seasonal windows:** check `${CLAUDE_PLUGIN_ROOT}/references/maintenance-tasks.md` for windows opening for the user's area (for example first frost in late fall). When unsure of the local timing, do a quick web search. When a window opens, give the task a concrete Next due.
- **Follow-ups from the log:** anything the last entries said to re-check ("re-test hardness in a week").

## 2. Write the check-in

Format, in this order, leaving out empty sections:

1. One opening line ("Quiet week, just one thing." / "Three things this week, about 20 minutes total.")
2. **This week:** each task with a one-line how-to and time needed.
3. **Coming up:** with any prep to do now.
4. **Seasonal heads-up**, if a window is opening.
5. Close with: "Anything acting weird around the house, or anything you did that I should log?"

Keep the whole thing short enough to read on a phone. Group tasks into one session where possible ("Saturday morning, 20 minutes: salt, filter, alarm test").

## 3. Handle the reply

- **"I did X":** log it (home-log skill) and update the matching task's Last done and Next due. Confirm in one line.
- **Something seems off** ("the dishwasher is making a noise"): switch to troubleshooting (is-it-broken skill).
- **"Skip" or "not this week":** push Next due by a week and say so.
- **Nothing:** end with a one-line sign-off.

## 4. To-do list

If the profile names a to-do list the user keeps (for example a Notion database) and the tools to reach it are available, add the This week tasks to it with due dates, unless they're already there. Mention that you did, in one line. Don't duplicate items on later check-ins.
