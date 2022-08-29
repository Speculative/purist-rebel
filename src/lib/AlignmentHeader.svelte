<script lang="ts">
  import Editable from "./Editable.svelte";

  export let alignment: "Purist" | "Neutral" | "Rebel";
  export let axis: string;
</script>

<div class={alignment}>
  <h2><Editable bind:text={axis} /> {alignment}</h2>
  <p><Editable text="Description goes here" /></p>
</div>

<style>
  div {
    padding: 1rem;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  h2 {
    text-align: center;
  }

  .Purist h2 {
    color: #214a08;
  }

  .Neutral h2 {
    color: #7e5d10;
  }

  .Rebel h2 {
    color: #731410;
  }

  p {
    text-align: center;
  }
</style>
