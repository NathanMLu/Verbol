<script lang="ts">
  import Icon from "@iconify/svelte";

  import Predictionary from "predictionary";

  let predictionary = Predictionary.instance();
  predictionary.addWords(["the", "be", "to", "of", "and", "a", "in", "that", "have", "it",
    "for", "not", "on", "with", "he", "as", "you", "do", "at", "this",
    "but", "his", "by", "from", "they", "we", "say", "her", "she", "or",
    "an", "will", "my", "one", "all", "would", "there", "their", "what",
    "so", "up", "out", "if", "about", "who", "get", "which", "go", "me",
    "when", "make", "can", "like", "time", "no", "just", "him", "know",
    "take", "people", "into", "year", "your", "good", "some", "could",
    "them", "see", "other", "than", "then", "now", "look", "only", "come",
    "its", "over", "think", "also", "back", "after", "use", "two", "how",
    "our", "work", "first", "well", "way", "even", "new", "want", "because",
    "any", "these", "give", "day", "most", "us"]);



  function predict(word: string) {
    let suggestions = predictionary.predict(word);
    console.log(suggestions);
    return suggestions;
  }

  function textToSpeech(name: string) {
    console.log("This has been clicked " + name);

    const msg = new SpeechSynthesisUtterance(name);
    const msg_2 = new SpeechSynthesisUtterance(predict(name))
    window.speechSynthesis.speak(msg);
    window.speechSynthesis.speak(msg_2);
  }
</script>

<div>
  <h1 class="font-semibold text-4xl">AAC Communication</h1>
  <p>Click on a word to hear it spoken. Based on what you say, we will try to predict what you want to say next.</p>

  <table class="table-auto mt-6">
    <tr>
      <td style="width: 100%;" class="flex flex-col align-middle">
        <div on:click={() => textToSpeech("Eat")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Eat</h3>
          <Icon icon="fluent-mdl2:eat-drink" class="w-10 h-10" />
        </div>
      </td>
      <td style="width: 10%;">
        <div on:click={() => textToSpeech("Bathroom")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Wash</h3>
          <Icon icon="cbi:roomsbathroom" class="w-10 h-10" />
        </div>
      </td>
      <td>
        <div on:click={() => textToSpeech("Yes")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Yes</h3>

          <Icon icon="healthicons:yes-outline" class="w-10 h-10" />
        </div>
      </td>

      <td>
        <div on:click={() => textToSpeech("No")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">No</h3>
          <Icon icon="dashicons:no" class="w-10 h-10" />
        </div>
      </td>

      <td>
        <div on:click={() => textToSpeech("Out")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Out</h3>
          <Icon icon="arcticons:clear-outside" class="w-10 h-10" />
        </div>
      </td>

      <td>
        <div on:click={() => textToSpeech("Up")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Up</h3>
          <Icon icon="ic:outline-expand-less" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Right")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Right</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="mdi:sleep" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Less")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Less</h3>
          <Icon icon="ic:outline-expand-more" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Stop")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Stop</h3>
          <Icon icon="openmoji:stop-sign" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("You")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">You</h3>
          <Icon icon="arcticons:daily-you" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Water")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Water</h3>
          <Icon icon="mdi:water" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Pet")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Pet</h3>
          <Icon icon="streamline:pet-paw" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Mom")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Mom</h3>
          <Icon icon="mdi:mom" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Dad")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Dad</h3>
          <Icon icon="mdi:father" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("TV")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">TV</h3>
          <Icon icon="mdi:television" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>

    <tr>
      <td>

      </td>
      <td>

      </td>
      <td>

      </td>

      <td>

      </td>

      <td>

      </td>

      <td>

      </td>
    </tr>



  </table>
</div>

<style>
  table {
    border-collapse: collapse;
  }
  td,
  th {
    border: 1px solid black;
    padding: 8px;
  }
</style>
