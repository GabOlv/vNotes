<script lang="ts">
  import { getCurrentWindow } from '@tauri-apps/api/window';
  
  // Initialize the window API
  const appWindow = getCurrentWindow();

  // Props using Svelte 5 Runes
  let { sidebarOpen = $bindable() }: { sidebarOpen: boolean } = $props();

  // Window Action Handlers
  async function handleMinimize() {
    await appWindow.minimize();
  }

  async function handleToggleMaximize() {
    await appWindow.toggleMaximize();
  }

  async function handleClose() {
    await appWindow.close();
  }
</script>

<div class="dock-container">
  <header class="top-bar" data-tauri-drag-region>
    <div class="left-section">
      <button 
        class="menu-toggle" 
        class:active={sidebarOpen} 
        onclick={() => sidebarOpen = !sidebarOpen}
        title="Toggle Sidebar"
      >
        ☰
      </button>
      <span class="app-title">Notes</span>
    </div>

    <div class="window-controls">
      <button class="control-btn" onclick={handleMinimize} title="Minimize">
        <svg width="12" height="12" viewBox="0 0 12 12">
          <rect fill="currentColor" x="1" y="5.5" width="10" height="1"/>
        </svg>
      </button>
      
      <button class="control-btn" onclick={handleToggleMaximize} title="Maximize">
        <svg width="12" height="12" viewBox="0 0 12 12">
          <rect fill="none" stroke="currentColor" stroke-width="1" x="2.5" y="2.5" width="7" height="7"/>
        </svg>
      </button>
      
      <button class="control-btn close-btn" onclick={handleClose} title="Close">
        <svg width="12" height="12" viewBox="0 0 12 12">
          <path fill="none" stroke="currentColor" stroke-width="1.2" d="M1.5 1.5l9 9M10.5 1.5l-9 9"/>
        </svg>
      </button>
    </div>
  </header>

  <nav class="side-bar">
    <div class="nav-top">
      <button class="add-btn" title="Add New">+</button>
    </div>
    
    <div class="nav-bottom">
      <button class="settings-btn" title="Settings">⚙</button>
    </div>
  </nav>
</div>

<style>
  .dock-container {
    grid-column: 1 / span 2;
    grid-row: 1 / span 2;
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-template-rows: 40px 1fr;
    pointer-events: none; /* Let clicks pass through to content */
  }

  .top-bar, .side-bar {
    background: var(--dock);
    pointer-events: auto; /* Re-enable clicks for buttons */
  }

  .top-bar {
    grid-column: 1 / span 2; /* Occupies full width */
    grid-row: 1;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 10px;
    border-bottom: 1px solid var(--border);
    -webkit-app-region: drag; /* Draggable window region */
    z-index: 20;
  }

  .left-section {
    display: flex;
    align-items: center;
    gap: 12px;
    -webkit-app-region: no-drag;
  }

  .app-title {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--muted);
    font-weight: 600;
  }

  .window-controls {
    display: flex;
    height: 100%;
    -webkit-app-region: no-drag; /* Ensure buttons remain clickable */
  }

  .side-bar {
    grid-column: 1;
    grid-row: 2; /* Positioned below the Top Bar */
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    padding: 20px 0;
    border-right: 1px solid var(--border);
    z-index: 10;
  }

  .nav-top, .nav-bottom {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  /* Universal Button Styles */
  button {
    width: 32px;
    height: 32px;
    background: transparent;
    border: none;
    color: var(--muted);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 6px;
    transition: all 0.15s ease;
  }

  button:hover {
    background: rgba(255, 255, 255, 0.08);
    color: var(--text);
  }

  /* Window Control Specifics */
  .control-btn {
    width: 46px; /* Mimic Windows hitboxes */
    height: 100%;
    border-radius: 0;
  }

  .close-btn:hover {
    background: #e81123 !important;
    color: white !important;
  }

  .menu-toggle.active {
    color: var(--accent);
  }

  .add-btn {
    font-size: 24px;
    font-weight: 300;
  }
</style>