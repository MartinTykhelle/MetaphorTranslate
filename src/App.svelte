<script>
  import Keyboard from "./lib/Keyboard.svelte";

  let metaphorText = "";
  let letters = [
    ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"],
    ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k"],
    ["l", "m", "n", "o", "p", "r", "s", "t", "u", "v", "z"],
    [" "],
  ];
  let regexp = new RegExp(`[^${letters.flat().join("")}]`, "gi");

  function addLetter(event) {
    metaphorText = metaphorText + event.detail.key;
    filterLetters();
  }
  function filterLetters() {
    metaphorText = metaphorText.replace(regexp, "").toUpperCase();
  }
</script>

<main>
  <div>
    <textarea
      class="metaphor"
      bind:value={metaphorText}
      on:keyup={filterLetters}
    ></textarea>
  </div>
  <div id="google_translate_element" class="translate">
    <textarea class="translated" bind:value={metaphorText} readonly="readonly"
    ></textarea>
  </div>
  <a
    href="https://translate.google.com/?sl=eo&tl=en&text={metaphorText}&op=translate"
    target="_blank">Translate with google</a
  >

  <Keyboard {letters} on:keyboardClicked={addLetter}></Keyboard>
</main>

<style>
  .metaphor {
    font-family: metaphor;
  }
  .translated {
    border: black;
    resize: none;
    outline: none;
  }
  textarea {
    height: 60px;
    width: 80%;
  }
</style>
