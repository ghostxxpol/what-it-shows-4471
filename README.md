# what-it-shows-4471

MEGA.dev S01E03. Support ticket #4471 merged 412 date reports into one issue. It holds two problems:

| Issue | Problem | Reports |
|---|---|---|
| [#1](../../issues/1) | `parser`: month-first parsing for day-first tenants (5 of these read as a one-day move) | 379 |
| [#2](../../issues/2) | `hint`: booking-v3 prints MM/DD/YYYY for day-first tenants | 33 |

Issue 3 was closed: the desk counts those 5 reports under `parser`.

The kb page for the desk:

- `src/routes/kb/incidents/4471-problems/+page.svx`: the page (signed `ghostxxpol`; uses the desk's own `CauseTable`)
- `rendered/4471-problems.html`: the page as the desk will see it

Prepared with AI assistance; reviewed and validated by ghostxxpol.
