<script>
  import HebrewLetters from "$lib/components/HebrewLetters.svelte";
  import HebrewInputComponent from "$lib/components/HebrewInputComponent.svelte";
  import { onMount } from "svelte";
  let letters = [];

  onMount(async () => {
    const response = await fetch("/hebrew-letters.json");
    letters = await response.json();
  });
</script>

<h1 class="text-4xl my-4 text-white text-center">Hebrew Meanings</h1>

<div class="m-4 text-white">
  <HebrewInputComponent {letters} />
  <HebrewLetters />
</div>
