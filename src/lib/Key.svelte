<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let key;
  let keyClass = " ";

  key = key.toUpperCase();

  if (key == " ") {
    keyClass = "space";
  }

  function click() {
    console.log(key);
    dispatch("keyboardClicked", { key: key });
  }
</script>

<button onclick={click} class={keyClass}>
  {key}
</button>

<style>
  button {
    width: 50px;
    height: 50px;
    font-size: 38px;
    padding: 0px;
    margin: 3px;
  }
  .space {
    width: 400px;
  }
</style>
