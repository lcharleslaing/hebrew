<script>
  import { onMount } from "svelte";

  let letters = [];

  onMount(async () => {
    const response = await fetch("/hebrew-letters.json");
    letters = await response.json();
  });
</script>

<div
  class="container mx-auto p-4 grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-4"
>
  {#each letters as letter}
    <div class="card rounded-xl bg-base-100 shadow-xl">
      <div class="card-body bg-slate-800 rounded-xl">
        <h2 class="card-title text-6xl justify-center font-bold">
          {letter.letter}
        </h2>
        <p class="text-lg text-center">{letter.name}</p>
        <p class="text-center text-2xl">{letter.numericalValue}</p>
        <div class="text-xs">
          <ul class="uppercase text-center text-md font-bold">
            {#each letter.meaning as meaning}
              <li>{@html meaning},</li>
            {/each}
          </ul>
        </div>
      </div>
    </div>
  {/each}
</div>
