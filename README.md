# AI model test prompts

The prompts from the tests on my YouTube channel, [@brennenbarney](https://www.youtube.com/@brennenbarney), word for word. Every model in a test gets the same prompt, so you can run them on anything you like and compare.

| Test | Prompt | What it asks for | Video |
|---|---|---|---|
| Bloons Tower Defense | [prompt](bloons-td/prompt.md) | A full Bloons-style game in the browser | [I Burned 1.4 Billion Tokens Testing AI Effort Levels](https://youtu.be/OVToi81LBSI), Kimi K3.1 Pro tested |
| Bloons, as a team | [Claude subagents](bloons-td/team-claude-subagents.md), [GPT-6 Luna subagents](bloons-td/team-luna-subagents.md) | The same game, with a planner handing all the code to cheaper subagents | Haiku 5.5 |
| Gummy bears | [prompt](gummy-bears/prompt.md) | Translucent jelly bears you can grab, stretch, squash, throw and pour | Gemini 4 Argon, Kimi K3.1 Pro tested |
| Landing page | [short brief](fernway-landing-page/prompt-short.md), [long brief](fernway-landing-page/prompt-long.md) | A waitlist page for Fernway, a made-up HR startup | Design skills test, Kimi K3.1 Pro tested (short brief) |
| Notion clone | [prompt](notion-clone/prompt.md) | A working Notion-style web app, from one prompt | [Is GPT-6 Astra AGI?](https://www.youtube.com/watch?v=n_rz6KYmy9k), [Fable 5.1 vs GPT-6 Astra](https://www.youtube.com/watch?v=VhmEGMG2xgY) |
| Jev vs Laya vs Haiku | [questions](jev-vs-laya/questions.md) | Sorting emails and support tickets, and guessing a review's stars | [I Tested Jev](https://youtu.be/iHC3YEZ8XKU) |
| Token savers | [sqlite-utils issues](token-savers/sqlite-utils-maintainer.md), [data analysis](token-savers/data-analysis.md), [data dashboard](token-savers/data-dashboard.md) | Real coding and data tasks, to measure what token-saving add-ons change | No video yet |
| Does planning help? | [base](planning-experiment/prompt-base.md), [with Syntaur](planning-experiment/prompt-syntaur.md), [Calculator spec](planning-experiment/spec-calculator.md), [Snippets spec](planning-experiment/spec-snippets.md) | The same feature with and without a planning step | No video yet |
| REA setup | [prompt](rea/setup.md) | Setting up the REA reverse-engineering tools | REA |

## Running them

Start each one in an empty folder, with no project instructions the model could lean on.

- **Bloons:** the line starting "Other programs on this machine" was added on 2026-10-13, after a run stopped every other node process on my machine. Runs before that date had the same prompt without that line.
- **Gummy bears:** this started from a prompt someone posted on Reddit.
- **Landing page:** put the [`brand`](fernway-landing-page/brand) folder next to the prompt, since the brief points to the logo there.
- **Notion clone:** started with `/goal`, in a folder holding Firebase and Supabase project config. You'll need your own.
- **Jev vs Laya:** the test items aren't here. The emails came from a real inbox and the reviews from real people.
- **Token savers:** these need files that aren't here. The sqlite-utils task runs on a snapshot of that repo with four real bugs put back, and the data tasks use nflverse play-by-play and FRED series.
- **Does planning help?:** `{{SPEC}}`, `{{TICKET}}` and `{{PROJECT}}` get filled in per run. One group starts in plan mode with the base prompt, one uses the Syntaur version, and one runs in auto mode with the base prompt. The specs are written against my own Raycast rebuild.
