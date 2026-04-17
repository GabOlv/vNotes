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
    width: 50px;
    background: #111;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 8px;
  }

  button {
    background: none;
    border: none;
    color: white;
    cursor: pointer;
    font-size: 18px;
  }

  .bottom {
    margin-top: auto;
  }
</style>