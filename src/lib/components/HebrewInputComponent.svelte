<script>
  import { onMount } from "svelte";
  import HebrewCharacterCard from "$lib/components/HebrewCharacterCard.svelte";

  export let letters = []; // Ensure this line is present
  let inputText = "";
  let characterMeanings = [];

  // Load the last input value from localStorage
  onMount(() => {
    const savedInput = localStorage.getItem("lastInput") || "";
    inputText = savedInput;
    processInput();
  });

  function processInput() {
    console.log("Processing input: ", inputText); // Log the input text
    characterMeanings = inputText
      .split("")
      .map((char) => {
        const foundLetter = letters.find((letter) => letter.letter === char);
        console.log("Found letter for char " + char + ":", foundLetter); // Log each found letter
        return foundLetter;
      })
      .filter(Boolean);
    console.log("Updated character meanings:", characterMeanings); // Log the updated character meanings
  }

  // Save input text to localStorage whenever it changes
  $: if (inputText) {
    console.log("Letters array:", letters);
    localStorage.setItem("lastInput", inputText);
    processInput();
  }

  // Function to clear the input and remove saved value from localStorage
  function clearInput() {
    inputText = "";
    characterMeanings = [];
    localStorage.removeItem("lastInput");
  }
</script>

<input
  type="text"
  bind:value={inputText}
  on:input={processInput}
  class="input input-bordered w-full max-w-xs"
  dir="rtl"
/>

<button on:click={clearInput} class="btn btn-primary"> Clear </button>

<div class="text-white flex overflow-x-auto py-2">
  {#each characterMeanings as char}
    <HebrewCharacterCard {char} />
  {/each}
</div>
