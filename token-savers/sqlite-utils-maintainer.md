You're a maintainer of sqlite-utils, the Python library and CLI in this folder. Work through the five issues below, then answer one question from a teammate.

The Python environment is ready: run Python as `.venv/bin/python` and the tests as `.venv/bin/pytest`. The full test suite takes about ten seconds.

## Issues

**1. `offset` doesn't work without `limit`**

`table.rows_where(offset=10)` crashes:

```
sqlite3.OperationalError: near "10": syntax error
```

It only works if I also pass `limit=`. I want to skip the first N rows and get all the rest. `sqlite-utils rows data.db mytable --offset 10` fails the same way unless I add `--limit`. Offset should work without a limit everywhere offset is accepted.

**2. `default_values` returns strings for TRUE, FALSE and NULL**

For a column declared `enabled integer default TRUE`, `db.table("t").default_values` returns `{"enabled": "TRUE"}`, a string. The same happens with `FALSE` and `NULL`. They should come back as `True`, `False` and `None`. Because of this, `table.create(..., defaults={"enabled": True}, transform=True)` rebuilds the table every time it runs, even when nothing changed.

**3. Empty strings survive a transform to a numeric type**

I imported a CSV with blank cells into a TEXT column, then ran `table.transform(types={"age": int})`. The blank cells are still `''` in the new INTEGER column, so sums and comparisons give odd results. When a TEXT column becomes INTEGER, FLOAT or REAL, empty strings should become NULL.

**4. `convert --dry-run` fails on names containing `]`**

```
sqlite-utils convert data.db 'table]name' 'column]name' 'value.upper()' --dry-run
```

fails with `sqlite3.OperationalError: unrecognized token: "]"`. The same command without `--dry-run` works.

**5. JSON output for `analyze-tables`**

`sqlite-utils analyze-tables` only prints a report for humans, so I can't feed it to other tools. Add a `--json` option that prints the analysis as a JSON array instead: one object per analyzed column, in the same order as the report, with the fields `table.analyze_column()` returns (`table`, `column`, `total_rows`, `num_null`, `num_blank`, `num_distinct`, `most_common`, `least_common`). The common-value lists become lists of `[value, count]` pairs, or `null` when there are none. It has to work with the command's existing options.

## Question from a teammate

"When I run `sqlite-utils insert data.db places places.csv --csv`, how does it decide each column's type? And how do I make sure the zip code column keeps its leading zeros?"

## Rules

- Commit each issue separately, with a message that starts with `#1:`, `#2:` and so on. Add or update tests for each one, and leave the full test suite passing.
- Work only inside this folder. Don't look anything up online, including this project's own repository or issue tracker.
- If you start a server or background process, stop it by its PID, never by process name.
- Nobody will answer questions while you work, so make your own decisions and finish the job.

When you're done, your final message is all your teammate will read. It must answer their question and say what you changed.
