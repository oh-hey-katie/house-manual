---
name: setup
description: This skill should be used when the user wants to set up their house in the house-manual plugin, start tracking home maintenance, or says things like "set up my house", "set up home maintenance", "I just moved in", "add my furnace", or "I got a new dishwasher". Also used when the check-in skill finds no house profile yet.
---

# Setup

Get the house into the plugin in about five minutes so the weekly check-in knows what to track. This is not a manual-building exercise: no appliance write-ups, no hunting for manuals. Only collect what decides which tasks apply.

Read `${CLAUDE_PLUGIN_ROOT}/references/storage.md` first and pick the backend.

## Interview

Ask one or two questions at a time, conversationally, not as a form. Skip anything already known.

1. City or region (for seasonal timing). Not the street address.
2. Home type (detached, semi, townhouse, condo) and roughly how old.
3. Heating and cooling: gas furnace, heat pump, boiler, baseboard, central AC, none.
4. Water: city or well? Water softener? Water heater tank or tankless? Sump pump?
5. Anything else they look after: gutters, outdoor faucets, ceiling fans, dishwasher, dryer.
6. Do they already keep a to-do list somewhere (for example a Notion database)? If yes, note its name (plain text, not a link) in the profile so the check-in can add due tasks there.
7. For tasks they remember doing recently ("I changed the filter in September"), get the rough date.

Don't ask for brands or model numbers. If the user offers them, record them.

## Build the task list

1. Pull matching tasks from `${CLAUDE_PLUGIN_ROOT}/references/maintenance-tasks.md`.
2. Fill Last done from what the user remembered; otherwise leave it blank and set Next due to a sensible near date so the task gets picked up rather than looking overdue.
3. Set each task's Status from its Next due (30-day rule in storage.md).
4. Show the list in a short table and let the user drop or change anything. Then write it.
5. Write the profile and create the empty log (Notion database or `log.md`).

## Finish

Tell the user in two or three lines what's being tracked and what the first check-in will cover. If they want a weekly reminder, suggest scheduling the check-in (for example Sunday evening) when the session has scheduling tools.

## Adding or changing a system later

When the user mentions a new appliance or one that's gone ("got a new dishwasher", "we removed the softener"), update the profile and add or remove its tasks. Confirm in one line.
