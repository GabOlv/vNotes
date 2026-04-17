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
  background: var(--bg);
  color: var(--text);
  padding: 24px;
  font-size: 15px;
  line-height: 1.6;
  font-family: ui-monospace, SFMono-Regular, Menlo, monospace;
}
</style>