<script lang="ts">
  import Display from "./lib/Display.svelte";
  import Button from "./lib/Button.svelte";
  const values = [
    "+",
    "1",
    "2",
    "3",
    "-",
    "4",
    "5",
    "6",
    "*",
    "7",
    "8",
    "9",
    "/",
    "C",
    "0",
    "=",
  ];
  function handleButtonClick(event: CustomEvent<{ value: string }>) {
    const value = event.detail.value;
  }
</script>

<main class="container">
  <div class="display">
    <Display />
  </div>
  <div class="grid buttons">
    {#each values as value}
      <div class="cell">
        <Button {value} on:click={handleButtonClick} />
      </div>
    {/each}
  </div>
</main>

<style>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100vh;
    width: 100vw;
  }
  .grid {
    display: grid;
    gap: 1rem;
    justify-items: center;
    margin-top: 1rem;
  }
  .buttons {
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(4, 1fr);
  }
</style>
