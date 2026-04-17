<script lang="ts">
  export let sidebarOpen: boolean;
</script>

<div class="dock">
  <button on:click={() => sidebarOpen = !sidebarOpen}>☰</button>

  <div class="bottom">
    <button>⚙</button>
  </div>
</div>

<style>
.dock {
 width: 40px;
 height: 100vh;
 background: var(--panel);
 display: flex;
 flex-direction: column;
 align-items: center;
 justify-content: space-between;
 padding: 10px 0;
 box-shadow: var(--shadow);
}

button {
 width: 40px;
 height: 40px;
 border-radius: 10px;
 border: none;
 background: transparent;
 color: var(--muted);
 cursor: pointer;
 transition: 0.15s ease;
}

button:hover 
{
 background: var(--panel-2);
 color: var(--text);
}

.bottom {
 margin-top: auto;
}
</style>