<script lang="ts">
  import Title from "./lib/Title.svelte";
  import Chart from "./lib/Chart.svelte";

  let subject = "Something";
</script>

<main>
  <Title bind:subject />
  <Chart {subject} />
</main>

<style>
  main {
    height: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
