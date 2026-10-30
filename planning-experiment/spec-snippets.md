# Feature: Snippets

Add Raycast's Snippets to Raycast Rebuild. It should behave like the real one:
save text you type often, insert it from the launcher, or type a short keyword
anywhere and have it expand.

## What it should do

- **Create Snippet**, a command in the launcher: a form with Name, Snippet (the
  text) and an optional Keyword.
  - Name and text are required.
  - A keyword has no spaces and must be unique; a duplicate gets a clear
    message.
- **Search Snippets**, a command in the launcher: lists your snippets with
  their keyword and a preview of the full text, and filters by name, keyword
  or text.
  - Enter pastes the chosen snippet into the app you were using.
  - The action panel (⌘K) can also copy, edit and delete one; delete asks
    first.
- Snippets also show up in the launcher's main search, by name and by
  keyword.
- **Placeholders** in snippet text are filled in when a snippet is used:
  - `{clipboard}`: the current clipboard text;
  - `{date}`, `{time}`, `{datetime}`: now;
  - `{cursor}`: where the text cursor ends up after inserting.
- **Keyword expansion:** typing a snippet's keyword in any other app replaces
  it with the snippet.
  - By default it only expands at the start of a word, not inside one. A
    setting allows expanding inside words.
  - Another setting turns expansion off.
  - It never expands inside Raycast Rebuild itself or in password fields.
  - Expansion needs the Accessibility permission. Without it, say so in Search
    Snippets; nothing should break.
- Using a snippet must not lose what was on the user's clipboard.
- Snippet text is the user's data: never log it.

## Element attributes (keep exactly; other tools rely on them)

- Search Snippets' search field has `aria-label="Search snippets"`.
- Each snippet row has a `data-snippet-name` attribute set to the snippet's name.
- The Create Snippet fields have the aria-labels `Name`, `Snippet` and
  `Keyword`.

## Environment note

This Mac runs Lockpaw, which drops synthetic hardware-level key events. If an
automated check can't make keyword expansion happen because of that, report
it as SKIP with the reason instead of failing.

## Done when

- It works in the real app as described.
- It has automated tests.
- All existing tests and `scripts/verify-phase6.sh` still pass.
