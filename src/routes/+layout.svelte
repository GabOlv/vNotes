<script lang="ts">
  import Dock from '$lib/components/Dock.svelte';
  import Sidebar from '$lib/components/Sidebar.svelte';
  import '../app.css';

  let sidebarOpen = $state(true);
</script>

<div class="app-layout">
  <Dock bind:sidebarOpen />
  
  <div class="main-content">
    <Sidebar {sidebarOpen} />
    <main class="editor">
      <slot />
    </main>
  </div>
</div>

<style>
  .app-layout {
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-template-rows: 40px 1fr;
    height: 100vh;
  }
  .main-content {
    grid-column: 2;
    grid-row: 2;
    display: flex;
  }
</style>