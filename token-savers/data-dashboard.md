# Build an interactive data dashboard

Build a dashboard that runs in the browser and lets people explore two datasets: NFL play-by-play for the 2023 and 2024 seasons, and market and economic series from the St. Louis Fed. The data is in `data/`, described in `data/README.md`. Python with pandas and numpy is ready as `.venv/bin/python`, and Node is installed too. Use any stack and any charting library you like.

## What it needs

The dashboard has two views, **NFL** and **Markets**, with a clear way to switch between them.

### NFL view

Filters: **team** (all 32), **season** (2023, 2024 or both) and **games** (regular season, playoffs or all). Every chart and number on the view follows the filters.

Numbers for the selected team, each in an element with the given `data-kpi` attribute:

| `data-kpi` | What it shows |
|---|---|
| `off-epa` | Offensive EPA per play: the mean `epa` of plays where the team is `posteam` and `play_type` is `pass` or `run`. Three decimals. |
| `def-epa` | Defensive EPA per play: the same, for plays where the team is `defteam`. Lower is better. Three decimals. |
| `fourth-attempts` | 4th-down plays with `play_type` `pass` or `run`. |
| `fourth-rate` | Share of those converted (`fourth_down_converted` is 1), as a percent with one decimal. |
| `record` | Wins and losses in the selected games, for example `12-5`, plus `-1` for ties only if there were any. A game's result comes from `result` (home score minus away score). |

Charts:

1. Every team's offensive against defensive EPA per play, with the selected team highlighted. Clicking a team selects it.
2. The selected team's offensive EPA per play in each game, in order, with the opponent and score on hover.
3. 4th-down attempts and conversion rate by yards to go (1, 2–3, 4–6, 7 or more), for the selected team against the league average.
4. A table of the top 10 passers by passing yards for the selected seasons and games, league-wide, sortable by any column.

### Markets view

A **date range** with presets for the last 1, 5 and 10 years (ending on the last date in the data) and a way to pick any start and end date. The default is the last 10 years. Every chart and number on the view follows the range.

| `data-kpi` | What it shows |
|---|---|
| `sp-change` | The S&P 500's percentage change from its first to its last close inside the range. Two decimals. |
| `max-drawdown` | The largest percentage fall of the S&P 500 from a running peak to a later close, both inside the range, as a negative percent with one decimal. |
| `inverted-days` | Days inside the range where both `DGS10` and `DGS2` have a value and the 10-year yield is below the 2-year yield. |

Charts:

1. The S&P 500, with its drawdown from the running peak below it on the same time axis.
2. The 10-year minus 2-year yield spread, with inverted stretches shaded.
3. Year-over-year CPI inflation and the federal funds rate, on one chart.
4. The S&P 500's monthly return against the monthly change in the 10-year yield, one point per month, with the correlation shown.

### Everywhere

- Hovering a chart shows exact values. Filters work from the keyboard.
- The URL records the current view and filters, so a copied link reopens the same state. Use these parameters: `view=nfl|markets`, `team=BAL` (the abbreviations in the data), `season=2023|2024|both`, `games=reg|post|all`, `start=YYYY-MM-DD` and `end=YYYY-MM-DD`. For example, `?view=nfl&team=BAL&season=2024&games=reg` or `?view=markets&start=2020-01-01&end=2020-12-31`.
- Numbers are formatted for people: thousands separators, percent signs and consistent decimals.
- It works in a browser window from 1024 to 1920 pixels wide, has a loading state, and uses colors that stay readable for color-blind viewers.

## Data and performance

The raw files are about 200 MB, so don't load them in the browser. Write a build step that turns `data/` into compact files for the dashboard, and keep everything the browser downloads, libraries included, under 5 MB. The dashboard has to open in about two seconds on this machine.

## Deliver

- One command that builds the data and serves the dashboard, plus the URL to open, in `README.md`.
- `NOTES.md` with your main design decisions and anything you left out or know is rough.
- Commit your work with git (`data/` and `.venv/` are already ignored).

## Rules

- Compute everything from the files in `data/`, and don't change them.
- Work only inside this folder. It must run locally with no accounts, API keys or paid services.
- If you start a server or background process, stop it by its PID or port before you finish, never by process name.
- Nobody will answer questions while you work, so make your own decisions and finish the job.
