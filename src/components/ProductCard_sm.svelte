<script lang="ts">
  export let name: string = 'nombre';
  export let description: string = '';
  export let price: number = 0;
  export let image: string = '';
  export let isNew: boolean = false;
</script>

<!-- Product Card: Marisco -->
<div class="flex gap-4 p-3 bg-surface-light dark:bg-surface-dark rounded-xl shadow-sm border border-primary/5">
    <div class="w-24 h-24 rounded-lg bg-cover bg-center shrink-0" style={`background-image: url('${image ?? ''}')`}></div>
  <div class="flex flex-col justify-between flex-1">
    <div>
          <h4 class="font-bold text-slate-900 dark:text-slate-100">{name} {#if isNew}<span class="text-[10px] bg-primary text-white px-1.5 py-0.5 rounded ml-1 uppercase">Nuevo</span>{/if}</h4>
          <p class="text-xs text-slate-500 dark:text-slate-400 line-clamp-2">{description}</p>
    </div>
    <div class="flex items-center justify-between mt-2">
        <span class="text-primary font-bold">{ '$' + (price ?? 0).toFixed(2) }</span>
      <button class="bg-primary hover:bg-primary/90 text-white p-1 rounded-lg flex items-center justify-center">
        <span class="material-symbols-outlined">add</span>
      </button>
    </div>
  </div>
</div>