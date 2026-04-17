<script lang="ts">
  let text = "";
</script>

<textarea bind:value={text} placeholder="Write your notes..." ></textarea>

<style>
  textarea {
    width: 100%;
    height: 100%;
    border: none;
    outline: none;
    resize: none;
    padding: 16px;
    font-size: 16px;
    font-family: monospace;
    background: #1e1e1e;
    color: white;
  }
</style>