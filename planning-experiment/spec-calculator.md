# Feature: Calculator

Add Raycast's Calculator to Raycast Rebuild. It should behave like the real
one: type a calculation into the launcher's search and get the answer right
there.

## What it should do

- When the search text is a calculation, show the answer as the first result,
  above everything else, together with the expression. Normal results still
  show below it.
- It handles:
  - **arithmetic**, including percentages (`15% of 80`, `80 + 15%`) and common
    functions and constants (`sqrt`, `round`, `sin`, `log`, `pi`, ...);
  - **unit conversions** with `in` or `to` (length, mass, temperature, volume,
    data size, time);
  - **simple date math** (`today + 3 days`, `days until 2026-12-25`, the
    difference between two dates).
- Decimal answers are exact where a person expects them to be (`0.1 + 0.2` is
  `0.3`). Show at most 10 decimal places, and thousands separators on screen.
- Anything that isn't a calculation (`safari`, a lone number like `2024`,
  half-typed or invalid input, division by zero) shows no calculator result
  and no error.
- Enter copies the answer (the plain value, without thousands separators). The
  action panel (⌘K) can also paste it into the app you were using.
- Copied or pasted answers are kept in a history you can open from the
  launcher ("Calculator History"), search, copy from and delete from.
- Typing must stay as fast as it is now.

## Examples

| Search text | Answer shown |
| --- | --- |
| `2+2` | `4` |
| `(3 + 4) * 2^3` | `56` |
| `0.1 + 0.2` | `0.3` |
| `15% of 80` | `12` |
| `80 + 15%` | `92` |
| `sqrt(144) / 3` | `4` |
| `1234.5 * 1` | `1,234.5` |
| `5 km in miles` | `3.1068559612 mi` |
| `72 f to c` | `22.2222222222 °C` |
| `1 gb in mb` | `1,000 MB` |
| `2 hours in minutes` | `120 min` |
| `safari` | (no calculator result) |
| `2024` | (no calculator result) |
| `1/0` | (no calculator result) |

## Required hooks (used by our own tests, keep exactly)

- The element that shows the answer has `data-testid="calculator-result"`, and
  its text is the answer as shown (for example `1,234.5`).
- The element that shows the expression has
  `data-testid="calculator-expression"`.
- When there is no answer, no `calculator-result` element exists.

## Done when

- It works in the real app as described.
- It has automated tests, including a check of the real app that runs as
  `scripts/verify-calculator.sh` (like the other `scripts/verify-*.sh`).
- All existing tests and `scripts/verify-phase6.sh` still pass.
