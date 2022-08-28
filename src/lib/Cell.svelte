<script lang="ts">
  export let r: number;
  export let c: number;
</script>

<div style:grid-row={`${r} / ${r + 1}`} style:grid-column={`${c} / ${c + 1}`}>
  <slot />
</div>

<style>
  div {
    color: black;
  }
</style>
