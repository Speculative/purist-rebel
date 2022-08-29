<script lang="ts">
  import AlignmentHeader from "./AlignmentHeader.svelte";
  import Alignment from "./Alignment.svelte";
  import Cell from "./Cell.svelte";

  export let subject: string;

  const alignments = ["Purist", "Neutral", "Rebel"] as const;

  let hAxis = "Structure";
  let vAxis = "Content";

  function range(length) {
    return Array.from({ length }, (_, i) => i);
  }
</script>

<div class="chart">
  <Cell r={1} c={1} />
  {#each range(3) as i}
    <Cell r={i + 2} c={1}>
      <AlignmentHeader alignment={alignments[i]} bind:axis={vAxis} />
    </Cell>
  {/each}

  {#each range(3) as i}
    <Cell r={1} c={i + 2}>
      <AlignmentHeader alignment={alignments[i]} bind:axis={hAxis} />
    </Cell>
  {/each}

  {#each range(3) as v}
    {#each range(3) as h}
      <Cell r={v + 2} c={h + 2}>
        <Alignment
          hAlign={alignments[h]}
          vAlign={alignments[v]}
          {hAxis}
          {vAxis}
          {subject}
        />
      </Cell>
    {/each}
  {/each}
</div>

<style>
  .chart {
    /* Fill all vertical space below title */
    flex-grow: 1;

    display: grid;

    grid-template-columns: 20rem 1fr 1fr 1fr;
    grid-template-rows: 10rem 1fr 1fr 1fr;

    column-gap: 0;
    row-gap: 0;

    overflow: hidden;
  }
</style>
