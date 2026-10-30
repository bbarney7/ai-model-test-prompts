You're a data analyst. The `data/` folder holds two datasets: NFL play-by-play for the 2023 and 2024 seasons, and market and economic series from the St. Louis Fed. `data/README.md` describes them. Answer the twelve questions below from these files, then write a short report.

Python with pandas, numpy and matplotlib is ready: run it as `.venv/bin/python`. You can install other packages into that environment if you want them.

## Questions

"Regular season" means rows where `season_type` is `REG`.

**NFL**

1. Which team had the highest offensive EPA per play in the 2024 regular season? Count only plays where `play_type` is `pass` or `run`, credit each play to `posteam`, and average `epa`.
2. In the 2024 regular season, how many 4th-down plays had `play_type` `pass` or `run`, how many of those were converted (`fourth_down_converted` is 1), and what was the conversion rate?
3. Which player had the most passing yards (`passing_yards`) across the 2023 and 2024 regular seasons combined, and how many?
4. What was the longest made field goal of the 2024 season, playoffs included, and who kicked it?
5. Across the 2023 and 2024 regular seasons, how many games were played, and what share did the home team win? A game counts as a home win when `result` is above 0.
6. What was the biggest comeback win of the 2024 regular season? Measure it as the largest point deficit, from `total_home_score` and `total_away_score` on any play, that the eventual winner overcame. Give the game, the winner and the deficit.

**Markets and the economy** (use the files exactly as they are; skip empty values)

7. What was the S&P 500's worst one-day percentage change in `SP500.csv`, close to close between consecutive trading days, and on what date?
8. What was the S&P 500's maximum drawdown in the file: the largest percentage fall from a running peak to a later low? Give the peak date, the trough date and the drawdown.
9. Across the whole history in `DGS10.csv` and `DGS2.csv`, what was the longest unbroken run of trading days on which the 10-year yield was below the 2-year yield? Count only days where both yields have a value. Give the first day, the last day and the number of trading days.
10. From the last S&P 500 close of 2019 to the last close of 2024, what was the index's percentage change, and what was it after inflation? For the inflation-adjusted figure, divide the 2024 close by the ratio of the December 2024 CPI value to the December 2019 value, then compare that with the 2019 close.
11. Between January 2022 and December 2023, inclusive, in how many months was the federal funds rate (`FEDFUNDS`) at least 0.20 percentage points higher than the month before?
12. What is the correlation between the S&P 500's monthly return and the monthly change in the 10-year yield, for each month from January 2017 to December 2025? Use the last available value in each calendar month for both series.

## Answers file

Compute every answer from the files, not from memory or the internet. Save your answers to `answers.json` in exactly this shape (percentages as percents, for example `-12.34`; rates and correlations as plain numbers; dates as `YYYY-MM-DD`; teams as the abbreviations in the data):

```json
{
  "q1":  {"team": "XXX", "epa_per_play": 0.000},
  "q2":  {"attempts": 0, "conversions": 0, "rate": 0.000},
  "q3":  {"player": "name as in the data", "yards": 0},
  "q4":  {"kicker": "name as in the data", "yards": 0},
  "q5":  {"games": 0, "home_win_rate": 0.000},
  "q6":  {"game_id": "", "winner": "XXX", "deficit": 0},
  "q7":  {"date": "YYYY-MM-DD", "pct_change": 0.00},
  "q8":  {"peak_date": "YYYY-MM-DD", "trough_date": "YYYY-MM-DD", "drawdown_pct": 0.00},
  "q9":  {"first_date": "YYYY-MM-DD", "last_date": "YYYY-MM-DD", "trading_days": 0},
  "q10": {"nominal_pct": 0.00, "real_pct": 0.00},
  "q11": {"months": 0},
  "q12": {"correlation": 0.000}
}
```

## Report

Write `REPORT.md` for a reader who knows sports and markets but not this data: your answers in one short table, then one interesting finding of your own choosing from each dataset, each with a chart saved as a PNG in this folder. Keep it under 600 words, and say plainly if anything in the data surprised you or made an answer uncertain.

## Rules

- Work only inside this folder, and don't change anything in `data/`.
- If you start a server or background process, stop it by its PID, never by process name.
- Nobody will answer questions while you work, so make your own decisions and finish the job.
