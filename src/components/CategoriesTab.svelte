<script>
  export let Links = [];
</script>

<style>
    .active-tab {
      background-color: #00bdd6;
      color: white;
    }

</style>

<!-- Categories Tab -->
<nav class="sticky top-17 z-40 bg-surface-light dark:bg-surface-dark border-b border-primary/10 shadow-sm">
  <div class="flex px-4 overflow-x-auto no-scrollbar">
    {#each Links as link, i}
      <a
        class={link.active
          ? "flex-none px-6 py-4 text-sm font-bold active-tab transition-colors"
          : "flex-none px-6 py-4 text-sm font-bold text-slate-500 border-b-3 border-transparent hover:text-white hover:bg-primary-active transition-colors"}
        href={link.href}
      >
        {link.title}
      </a>
    {/each}
  </div>
</nav>

