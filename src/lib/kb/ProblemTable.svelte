<script lang="ts">
  import reports from '#lib/data/reports-4471.json';
  import notes from '#lib/data/desk-notes.json';
  import { causeOf, uniqueById, type Cause, type Report } from '#lib/kb/causes';
  import { tenantOf } from '#lib/kb/locales';

  let { ticket }: { ticket: number } = $props();

  // The desk's oneDayMove reports are a third problem: one day off, not month and day swapped.
  type Problem = Cause | 'shift';
  const problemOf = (r: Report): Problem | null =>
    notes.oneDayMove.includes(r.id) ? 'shift' : causeOf(r, tenantOf(r));

  const merged = $derived(uniqueById(reports as Report[]).filter((r) => r.mergedInto === ticket));
  const rows = $derived(
    (['parser', 'hint', 'shift'] as Problem[]).map((p) => ({
      problem: p,
      n: merged.filter((r) => problemOf(r) === p).length,
    })),
  );
  const unplaced = $derived(merged.filter((r) => problemOf(r) === null).length);
</script>

<p><strong>{merged.length}</strong> reports merged into #{ticket} · <strong>{rows.filter((r) => r.n).length}</strong> problems</p>

<table>
  <thead><tr><th>problem</th><th>reports</th></tr></thead>
  <tbody>
    {#each rows as r (r.problem)}
      <tr><td><code>{r.problem}</code></td><td>{r.n}</td></tr>
    {/each}
    {#if unplaced}<tr><td>unplaced</td><td>{unplaced}</td></tr>{/if}
  </tbody>
</table>
