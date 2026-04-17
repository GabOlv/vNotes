<script lang="ts">
  import { Window } from '@tauri-apps/api/window';
  const appWindow = Window.getCurrent();

  let { sidebarOpen = $bindable() }: { sidebarOpen: boolean } = $props();
</script>

<div class="dock-container">
  <div class="top-bar" data-tauri-drag-region>
    <div class="left-section">
      <button class="menu-toggle" class:active={sidebarOpen} onclick={() => sidebarOpen = !sidebarOpen}>
        ☰
      </button>
      <div class="app-title">Notes</div>
    </div>

    <div class="window-controls">
      <button onclick={() => appWindow.minimize()}>─</button>
      <button onclick={() => appWindow.toggleMaximize()}>▢</button>
      <button class="close" onclick={() => appWindow.close()}>✕</button>
    </div>
  </div>

  <div class="side-bar">
    <div class="nav-top">
      <button class="add-btn">+</button>
    </div>
    <div class="nav-bottom">
      <button class="settings-btn">⚙</button>
    </div>
  </div>
</div>

<style>
  .dock-container {
    grid-column: 1 / span 2;
    grid-row: 1 / span 2;
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-template-rows: 40px 1fr;
    pointer-events: none;
  }

  .top-bar, .side-bar {
    background: var(--dock);
    pointer-events: auto;
  }

  .top-bar {
    grid-column: 1 / span 2; /* Full width priority */
    grid-row: 1;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 10px;
    border-bottom: 1px solid var(--border);
    -webkit-app-region: drag;
    z-index: 20;
  }

  .left-section {
    display: flex;
    align-items: center;
    gap: 12px;
    -webkit-app-region: no-drag;
  }

  .app-title {
    font-size: 12px;
    font-weight: 600;
    color: var(--muted);
    letter-spacing: 0.5px;
  }

  .side-bar {
    grid-column: 1;
    grid-row: 2; /* Starts below the top bar */
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    padding: 15px 0;
    border-right: 1px solid var(--border);
    z-index: 10;
  }

  .window-controls {
    display: flex;
    gap: 4px;
    -webkit-app-region: no-drag;
  }

  /* Fix for the white buttons in your image */
  button {
    width: 32px;
    height: 32px;
    background: transparent; /* Explicitly transparent */
    border: none;
    color: var(--text);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 6px;
    transition: background 0.2s;
  }

  button:hover {
    background: rgba(255, 255, 255, 0.08);
  }

  .close:hover {
    background: #e81123 !important;
    color: white;
  }

  .menu-toggle.active {
    color: var(--accent);
  }
</style>