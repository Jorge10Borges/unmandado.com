<script>
  import { onMount } from 'svelte';
  let titulo = 'Unmandado.com';

  onMount(() => {
    const t = setTimeout(() => {
      titulo = 'close';
    }, 2000);
    return () => clearTimeout(t);
  });
</script>

<div class="flex items-center p-4 justify-between max-w-7xl mx-auto w-full">
  <div class="text-primary flex size-10 shrink-0 items-center justify-center rounded-lg bg-primary/10">
    <span class="material-symbols-outlined">menu</span>
  </div>
  <h2 class="text-slate-900 dark:text-slate-100 text-xl font-bold leading-tight tracking-tight flex-1 text-center">{titulo}</h2>
  <div class="flex w-10 items-center justify-end">
    <button class="flex size-10 items-center justify-center rounded-full bg-primary/10 text-primary">
      <span class="material-symbols-outlined">person</span>
    </button>
  </div>
</div>
