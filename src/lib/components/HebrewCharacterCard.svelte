<script>
  export let char = {};
</script>

<div class="text-white card p-1 bg-slate-900 mx-2 flex flex-col items-center">
  <span
    class="mr-2 card bg-white text-black font-extrabold px-2 pt-0 pb-2 text-4xl"
  >
    {char.letter}
  </span>
  <span class="text-xl">
    {char.numericalValue}
  </span>
  <span class="text-xs">
    Meanings: {char.meaning.join(", ")}
  </span>
</div>
