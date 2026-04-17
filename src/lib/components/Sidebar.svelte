<script lang="ts">
  export let sidebarOpen: boolean;
</script>

<div class="sidebar" class:open={sidebarOpen}>
  <h3>Notes</h3>
</div>

<style>
  .sidebar {
    width: 0;
    overflow: hidden;
    background: #2a2a2a;
    transition: width 0.2s ease;
  }

  .sidebar.open {
    width: 250px;
  }

  h3 {
    color: white;
    padding: 10px;
  }
</style>