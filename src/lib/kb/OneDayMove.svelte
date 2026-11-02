<script lang="ts">
  import notes from '#lib/data/desk-notes.json';
  import reports from '#lib/data/reports-4471.json';
  import { uniqueById, type Report } from '#lib/kb/causes';

  let { ticket }: { ticket: number } = $props();

  // The reports the desk read as a one-day move: no month/day swap, just a day off.
  const moved = $derived(uniqueById(reports as Report[]).filter((r) => r.mergedInto === ticket && notes.oneDayMove.includes(r.id)));
</script>

<p><strong>{moved.length}</strong> reports: {moved.map((r) => r.id).join(', ')}.</p>
