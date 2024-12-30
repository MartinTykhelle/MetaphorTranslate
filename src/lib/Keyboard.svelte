<script>
  import Key from "./Key.svelte";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  function addLetter(event) {
    dispatch("keyboardClicked", { key: event.detail.key });
  }

  export let letters = [[]];
</script>

<div class="keyboard">
  {#each letters as row}
    <div class="row">
      {#each row as letter}
        <Key key={letter} on:keyboardClicked={addLetter}></Key>
      {/each}
    </div>
  {/each}
</div>

<style>
  @font-face {
    font-family: metaphor;
    src: url(/fonts/metaphor.woff);
  }
  .row {
    display: flex;
    justify-content: center;
  }
  .keyboard {
    font-family: metaphor;
  }
</style>
