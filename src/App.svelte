<script lang="ts">
  import Display from "./lib/Display.svelte";
  import { display } from "./lib/Store.js";
  import Button from "./lib/Button.svelte";

  $display = "";
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
    const displayable = [
      "1",
      "2",
      "3",
      "4",
      "5",
      "6",
      "7",
      "8",
      "9",
      "0",
      "+",
      "-",
      "*",
      "/",
    ];
    const value = event.detail.value;
    if (displayable.includes(value)) {
      $display += value;
    } else {
      if (value === "=") {
        try {
          $display = eval($display) === Infinity ? "Error" : eval($display);
        } catch (e) {
          $display = "Error";
        }
      } else {
        $display = "";
      }
    }
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
