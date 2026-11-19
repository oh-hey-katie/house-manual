---
name: is-it-broken
description: This skill should be used when the user suspects something in their home isn't working, or says things like "is my water softener broken", "is this normal", "my furnace is making a noise", "the water tastes weird", "there's water on the floor", or "do I need to call someone".
---

# Is It Broken?

Help the user work out whether something is actually broken, what they can safely check or fix themselves, and when to call a pro. Calm, specific, and honest: "this is normal" is a great answer when it's true.

## Step 1: Safety first

Before troubleshooting, check for danger signs. If any are present, give the immediate action and stop:

- **Gas smell** (rotten eggs): don't flip switches; leave, then call the gas utility from outside.
- **CO alarm sounding**: get everyone out and call 911.
- **Water near electrical** (panel, outlets, a pooling appliance): don't touch it; shut off the breaker only if you can reach it while standing on a dry surface, otherwise call an electrician.
- **Burning smell, sparks, or scorch marks**: turn off power at the breaker.
- **Active flooding**: shut the main water valve (point to its location in the house profile if known).

## Step 2: Load what's known

Read `${CLAUDE_PLUGIN_ROOT}/references/storage.md` and load the house profile and recent log entries for this system. Recent history matters: "ran out of salt last month" or "power outage last week" often explains the symptom.

When the answer depends on the exact model (error codes, settings, how to start a manual cycle, known faults), ask for a **photo of the rating label or model sticker**, telling the user where it usually is:

| Appliance | Where the label usually is |
|---|---|
| Water softener | Back or side of the control head (top of the tall tank), or the side of the tank |
| Furnace | Inside the front panel door |
| Water heater | Side of the tank, about eye level |
| Central AC | Side of the outdoor unit |
| Dishwasher | Edge of the door or inside the tub rim |
| Washer and dryer | Inside the door or lid, or the back panel |

Read the brand, model, and serial from the photo, then look up the manual and known problems for that model with web search. Many serial numbers encode the manufacture date; decode it when the pattern is known and say how confident you are. Save the brand and model to the house profile so you don't have to ask again.

For a water softener, also read `references/water-softener.md`.

## Step 3: Diagnose like a good technician

1. Ask what they noticed, when it started, and whether anything changed (power outage, ran out of salt, new season, recent work).
2. Go from easiest and most likely to hardest: power, settings, supplies, obvious blockages, then parts.
3. Give **one check at a time**, with exactly where to look and what "good" and "bad" look like. Wait for the answer before the next check.
4. Prefer tests that give a clear yes/no (test strips, comparing two taps, listening during a manual cycle) over vibes.
5. When the cause is found, explain it in one or two sentences and give the fix.

## Step 4: Verdict

End with one of:

- **✅ Working normally**: explain why what they noticed is normal.
- **🔧 Fixable yourself**: steps, rough cost of parts, and how long it takes.
- **📞 Call a pro**: which kind of pro (plumber, HVAC tech, electrician, appliance repair), what to tell them so they don't get upsold, and a rough sense of urgency (today / this week / when convenient).
- **🤷 Not sure yet**: the one test or observation that would settle it, and when to check again.

If the appliance is near or past its typical lifespan and the repair is expensive, say so plainly so the user can weigh repair against replacement.

## Step 5: Record it

Log what happened, what was found, and what was done (home-log skill); just do it and confirm in one line. If the diagnosis needs a follow-up ("re-test hardness in a week"), put it in the log notes and add it as a task with a Next due date so the weekly check-in raises it. If a recurring task fell out of the diagnosis, add it to the task list.

## Boundaries

- Don't walk the user through work on gas lines, the electrical panel, or anything that requires a permit; explain what the pro will do instead.
- Say when an answer depends on the specific model and you couldn't confirm it.
