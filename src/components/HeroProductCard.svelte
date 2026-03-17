
<script lang="ts">
  export let badget: string = '';
  export let titulo: string = '';
  export let subtitulo: string = '';
  export let image: string = '';
</script>

<section class="@container px-4 py-4">
  <div class="relative overflow-hidden rounded-xl h-56 bg-primary/20">
    <div class="absolute inset-0 bg-cover bg-center" style="background-image: linear-gradient(0deg, rgba(15, 33, 35, 0.8) 0%, rgba(15, 33, 35, 0.2) 60%), url('{image}');"></div>
    <div class="absolute bottom-0 left-0 p-6">
      {#if badget}
        <span class="bg-primary text-white text-xs font-bold px-2 py-1 rounded mb-2 inline-block uppercase tracking-wider">{badget}</span>
      {/if}
      <h2 class="text-3xl font-bold text-white leading-tight">{titulo}</h2>
      <p class="text-slate-200 text-sm mt-1">{subtitulo}</p>
    </div>
  </div>
</section>
