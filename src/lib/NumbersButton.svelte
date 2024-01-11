<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let number = 0;
  function handleClick() {
    dispatch("click", { number });
  }
</script>

<button on:click={handleClick}>{number}</button>
