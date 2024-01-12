<script lang="ts">
  import { display } from "./Store.js";
  $display = "";
</script>

<p>
  {$display}
</p>

<style>
  p {
    display: flex;
    align-items: center;
    justify-content: right;
    font-size: 2rem;
    font-weight: bold;
    text-align: right;
    padding: 1rem;
    border: 1px solid black;
    border-radius: 5px;
    width: 300px;
    height: 50px;
    overflow-x: hidden;
  }
</style>
