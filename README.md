# House Manual

The house manual you never got, as a weekly check-in. For anyone running a home who keeps forgetting the furnace filter, the softener salt, and the outdoor taps before the first freeze.

## What it does

- **Setup (5 minutes):** tell Claude what's in your house (furnace, AC, softener, sump pump…). It builds a short, realistic list of maintenance tasks. No manuals to collect.
- **Weekly check-in:** what's due this week, what's coming up (with "buy a filter this week" lead time), seasonal heads-ups before they're urgent, and a chance to say "the dishwasher's making a weird noise."
- **Is it broken?:** describe what's going on and Claude walks you through checks one at a time, then tells you whether it's normal, a DIY fix, or time to call a pro. Snap a photo of the appliance label when the model matters.
- **Home log:** "I added salt today." Answers "when did I last…?" and keeps a record ready for contractors.

## Install

- **Claude desktop app:** download [`dist/house-manual.plugin`](dist/house-manual.plugin) and install it in Claude.
- **Claude Code:** clone this repo and start Claude Code with the plugin loaded:

  ```bash
  git clone https://github.com/oh-hey-katie/house-manual.git
  claude --plugin-dir ./house-manual
  ```

Then say "set up my house".

## Try it

- "Set up my house"
- "House check-in"
- "Is my water softener broken?"
- "Log that I replaced the furnace filter"
- "When did I last add salt?"

## Make it weekly

Schedule a recurring task (for example Sunday at 7:30 pm) that says: "Run my house check-in." Claude opens the check-in and you reply when you have a minute.

## Your data

- **With Notion connected:** a **House** page with your **House Tasks** (list, calendar, and a kanban board: Later → Next up → In progress → Done), a **Home Log**, and a short profile of the house.
- **Without Notion:** plain markdown files in a `House/` folder in your working folder.

Nothing is sent anywhere else except web searches for appliance manuals and local frost dates. Don't put your address, alarm codes, or account numbers in it.

## Included appliance guides

- Water softener

More coming. Contributions welcome.

## Disclaimer

General guidance only. For gas, electrical panel, or permit work, call a licensed professional.

## License

MIT
