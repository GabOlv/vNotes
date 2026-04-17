<script lang="ts">
  import Dock from '$lib/components/Dock.svelte';
  import Sidebar from '$lib/components/Sidebar.svelte';

  let sidebarOpen = true;
</script>

<div class="app">
  <Dock bind:sidebarOpen />

  <Sidebar {sidebarOpen} />

  <main class="editor">
    <slot />
  </main>
</div>

<style>
  .app {
    display: flex;
    height: 100vh;
    width: 100vw;
    overflow: hidden;
  }

  .editor {
    flex: 1;
    background: #1e1e1e;
  }
</style>