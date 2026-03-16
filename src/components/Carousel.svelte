<script>
  import { onMount, onDestroy } from 'svelte';
  import { fade } from 'svelte/transition';

  export let slides = [];
  export let interval = 4000;

  let current = 0;
  let timer;

  function next() {
    current = (current + 1) % slides.length;
  }

  function prev() {
    current = (current - 1 + slides.length) % slides.length;
  }

  onMount(() => {
    if (slides.length > 1) {
      timer = setInterval(next, interval);
    }
  });

  onDestroy(() => {
    if (timer) clearInterval(timer);
  });
</script>

<style>
  .carousel { position: relative; }
  .controls { position: absolute; inset: 0; align-items:center; justify-content:space-between; pointer-events:none }
  .controls button { pointer-events:all }
  .indicators { position:absolute; left:50%; transform:translateX(-50%); bottom:0.75rem; display:flex; gap:0.5rem }
  .dot { width:10px; height:10px; border-radius:9999px; background:rgba(255,255,255,0.5) }
  .dot.active { background:white }
  .overlay { position:absolute; inset:0; display:flex; align-items: flex-start; padding:1.5rem }
  .overlay-content { max-width:36rem }
</style>

<div class="carousel relative overflow-hidden rounded-2xl aspect-square md:aspect-21/9 bg-slate-200">
  {#if slides.length === 0}
    <slot />
  {:else}
    {#each slides as slide, i}
      {#if i === current}
        <div class="absolute inset-0 w-full h-full" transition:fade>
          <img src={slide.src} alt={slide.alt || ''} class="w-full h-full object-cover" />
          <div class="overlay bg-linear-to-r from-black/60 to-transparent text-white">
            <div class="bottom-0 overlay-content">
              {#if slide.pill}<span class="bg-white/20 backdrop-blur-md w-fit px-3 py-1 rounded-full text-xs font-bold mb-2 uppercase tracking-widest">{slide.pill}</span>{/if}
              {#if slide.title}<h3 class="text-3xl font-black mb-2 leading-tight">{slide.title}</h3>{/if}
              {#if slide.subtitle}<p class="text-white/80 font-medium max-w-xs mb-4">{slide.subtitle}</p>{/if}
              {#if slide.cta}<button class="bg-white text-primary font-bold py-2 px-6 rounded-lg w-fit shadow-lg">{slide.cta}</button>{/if}
            </div>
          </div>
        </div>
      {/if}
    {/each}

    <div class="controls hidden md:flex">
      <button on:click={prev} class="m-4 bg-white/90 text-slate-900 rounded-full p-2 shadow-md">⟨</button>
      <button on:click={next} class="m-4 bg-white/90 text-slate-900 rounded-full p-2 shadow-md">⟩</button>
    </div>

    <div class="indicators">
      {#each slides as _, idx}
        <button class:active={idx === current} class="dot" on:click={() => { current = idx; if (timer) { clearInterval(timer); timer = setInterval(next, interval); } }} aria-label={"Go to slide " + (idx+1)}></button>
      {/each}
    </div>
  {/if}
</div>
