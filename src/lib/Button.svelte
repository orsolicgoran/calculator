<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let value = "";
  function handleClick() {
    dispatch("click", { value });
  }
</script>

<button on:click={handleClick}>{value}</button>
