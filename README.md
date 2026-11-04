# what-it-shows-4471

MEGA.dev S01E03. Support ticket #4471 merged 412 date reports into one issue. It holds three problems:

| Issue | Problem | Reports |
|---|---|---|
| [#1](../../issues/1) | `parser`: month-first parsing for day-first tenants | 374 |
| [#2](../../issues/2) | `hint`: booking-v3 prints MM/DD/YYYY for day-first tenants | 33 |
| [#3](../../issues/3) | one-day shift, likely time zones (unconfirmed) | 5 |

The kb page for the desk:

- `src/routes/kb/incidents/4471-problems/+page.svx`: the page (signed `ghostxxpol`)
- `src/lib/kb/ProblemTable.svelte`: the component that computes the counts
- `rendered/4471-problems.html`: the page as the desk will see it

Prepared with AI assistance; reviewed and validated by ghostxxpol.
