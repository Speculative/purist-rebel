<script lang="ts">
  import Editable from "./Editable.svelte";

  export let hAlign: "Purist" | "Neutral" | "Rebel";
  export let vAlign: "Purist" | "Neutral" | "Rebel";
  export let hAxis: string;
  export let vAxis: string;
  export let subject: string;
</script>

<section class={`h${hAlign} v${vAlign}`}>
  <h3>
    {#if hAlign === "Purist" && vAlign === "Purist"}
      Hardline Traditionalists
    {:else if hAlign === "Neutral" && vAlign === "Neutral"}
      True Neutral
    {:else if hAlign === "Rebel" && vAlign === "Rebel"}
      Radical <Editable text="Something" /> Anarchy
    {:else}
      {hAxis} {hAlign}, {vAxis} {vAlign}
    {/if}
  </h3>
  <div class="wrap" contenteditable="true" />
  <p>
    &ldquo;<Editable text="Something" /> is a {subject}.&rdquo;
  </p>
</section>

<style>
  section {
    width: 100%;
    height: 100%;
    padding: 0.5rem;

    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  .vPurist.hPurist {
    background: #818181;
  }

  .vPurist.hNeutral,
  .vNeutral.hPurist {
    background: #727272;
  }

  .vPurist.hRebel,
  .vNeutral.hNeutral,
  .vRebel.hPurist {
    background: #595959;
  }

  .vNeutral.hRebel,
  .vRebel.hNeutral {
    background: #454545;
  }

  .vRebel.hRebel {
    background: #303030;
  }

  h3 {
    font-size: 1.5rem;
    text-align: center;
    color: white;
    text-shadow: 0.1em 0.1em 1em rgba(0, 0, 0, 0.7);
  }

  .wrap {
    flex: 1 1 0;
    overflow: hidden;
    text-align: center;
  }

  :global(.wrap img) {
    max-width: 100%;
    max-height: 100%;
    height: auto;
    object-fit: contain;
  }

  p {
    font-size: 1.2rem;
    text-align: center;
    color: white;
    text-shadow: 0.1em 0.1em 1em rgba(0, 0, 0, 0.7);
  }
</style>
