<script lang="ts">
    let userInput = '';
    let nextWords = [
        "sad",
      "vacant",
      "weightless",
      "whale",
      "zany",
      "jasmine",
      "macro",
      "knapsack",
      "rabbit",
      "tactile",
      "vanish",
      "achoo",
      "father",
      "launch",
      "macho",
      "patrol",
      "taboo",
      "beachfront",
      "healer",
      "legion",
      "peaceful",
      "sheepdog",
      "thyme",
      "vibrant",
      "ghost",
      "hoagie",
      "locust",
      "motion",
      "romance",
      "vogue",
      "whopper",
    ];


    function addWord() {
        nextWords = [userInput, ...nextWords];
        userInput = '';
    }

</script>

<div>
    <h1 class="font-semibold text-4xl">Settings</h1>
    <p>Verbol is a communication tool for people with speech disabilities.</p>
</div>

<div class="config-panel mt-5">
    <div class="flex justify-start items-center gap-x-4">
        <input type="text" bind:value={userInput} placeholder="Enter a word" class="border-2 border-gray-300 rounded-md p-2" />
        <button on:click={addWord} class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            Add Word
        </button>
    </div>


  <div class="word-list mt-6">
    <h3 class="font-semibold text-2xl">
        Words:
    </h3>
    <!-- scroll if the words are too many -->
    <div class="scroll-box h-96 overflow-y-scroll mt-2">
      <ul>
        {#each nextWords as word}
          <li>{word}</li>
        {/each}
      </ul>
    </div>
  </div>
</div>

<style>
  
</style>