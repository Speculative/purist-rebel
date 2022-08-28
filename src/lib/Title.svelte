<script lang="ts">
  import Editable from "./Editable.svelte";
  export let subject: string;
</script>

<h1>The <Editable bind:text={subject} /> Alignment Chart</h1>

<style>
  h1 {
    text-transform: uppercase;
    text-align: center;
    background: #e5e5e5;
    color: #a8a8a8;
    font-size: 3rem;

    padding: 1.5rem;
  }
</style>
