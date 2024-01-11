<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let operation = "";
  function handleClick() {
    dispatch("click", { operation });
  }
</script>

<button on:click={handleClick}>{operation}</button>

<style>
  button {
    width: 50px;
    height: 40px;
  }
</style>
