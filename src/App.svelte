<script lang="ts">
  import NumbersButton from "./lib/NumbersButton.svelte";
  import OperationsButton from "./lib/OperationsButton.svelte";
  const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
  const operations = ["+", "-", "*", "/", "%"];
  function handleNumbersButtonClick(event: CustomEvent<{ number: number }>) {
    const number = event.detail.number;
  }
  function handleOperationsButtonClick(
    event: CustomEvent<{ operation: string }>
  ) {
    const operation = event.detail.operation;
  }
</script>

<main class="container">
  <div class="row">
    <div class="grid numbers">
      {#each numbers as number}
        <div class="cell">
          <NumbersButton {number} on:click={handleNumbersButtonClick} />
        </div>
      {/each}
    </div>
  </div>
  <div class="row">
    <div class="grid operations">
      {#each operations as operation}
        <div class="cell">
          <OperationsButton
            {operation}
            on:click={handleOperationsButtonClick}
          />
        </div>
      {/each}
    </div>
  </div>
</main>

<style>
  .container {
    display: flex;
    justify-content: center;
    align-items: start;
    flex-direction: row;
  }
  .grid {
    display: grid;
    gap: 10px;
    margin-top: 10rem;
  }
  .numbers {
    grid-template-columns: repeat(3, minmax(0, max-content));
  }
  .operations {
    margin-left: 10px;
    grid-template-columns: repeat(2, minmax(0, max-content));
    grid-template-rows: repeat(3, minmax(0, max-content));
  }
  .cell {
    display: flex;
    justify-content: center;
  }
  .cell:nth-child(10) {
    grid-column: span 3;
  }
</style>
