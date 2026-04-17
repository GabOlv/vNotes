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
  background: var(--panel);
  border-right: 1px solid var(--border);
  transition: width 0.2s ease;
}

.sidebar.open {
  width: 260px;
}

h3 {
 color: white;
 padding: 10px;
}
</style>