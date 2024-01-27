<script lang="ts">
  import Icon from "@iconify/svelte";

  import Predictionary from "predictionary";

  let predictions = [];

  let predictionary = Predictionary.instance();
  predictionary.addWords(["more"]);



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
    // window.speechSynthesis.speak(msg_2);

    predictions = predict(name);
    console.log(predictions)
    // window.speechSynthesis.speak(msg_2);
  }
</script>

<div>
  <h1 class="font-semibold text-4xl">AAC Communication</h1>
  <p>Click on a word to hear it spoken.</p>

  <table class="table-auto mt-6">
    <tr>
      <td style="width: 100%;" class="flex flex-col align-middle">
        <div on:click={() => textToSpeech("Eat")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Eat</h3>
          <Icon icon="fluent-mdl2:eat-drink" class="w-10 h-10" />
        </div>
      </td>
      <td style="width: 10%;">
        <div on:click={() => textToSpeech("Wash")} class="flex flex-col items-center justify-center">
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
        <div on:click={() => textToSpeech("Bus")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Bus</h3>
          <Icon icon="mdi:bus" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("What")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">What</h3>
          <Icon icon="logos:whatwg" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Phone")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Phone</h3>
          <Icon icon="ic:baseline-phone" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Math")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Math</h3>
          <Icon icon="material-symbols:table" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Today")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Today</h3>
          <Icon icon="material-symbols:today" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Sleep")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Sleep</h3>
          <Icon icon="icon-park:right" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Maybe")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Maybe</h3>
          <Icon icon="material-symbols:gpp-maybe" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Apple")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Apple</h3>
          <Icon icon="emojione:red-apple" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Pear")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Pear</h3>
          <Icon icon="fluent-emoji:orange-circle" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Read")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Read</h3>
          <Icon icon="ant-design:read-outlined" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Glass")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Glass</h3>
          <Icon icon="mdi:glass" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Time")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Time</h3>
          <Icon icon="mingcute:time-fill" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Play")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Play</h3>
          <Icon icon="ri:game-fill" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Cash")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Cash</h3>
          <Icon icon="material-symbols:money" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Song")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Song</h3>
          <Icon icon="streamline:music-folder-song" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Car")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Car</h3>
          <Icon icon="mdi:car" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Beach")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Beach</h3>
          <Icon icon="mdi:beach" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Fly")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Fly</h3>
          <Icon icon="tabler:plane" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("More")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">More</h3>
          <Icon icon="material-symbols:more" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Book")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Book</h3>
          <Icon icon="material-symbols:book" class="w-10 h-10" />
        </div>

      </td>
    </tr>

    <tr>
      <td>
        <div on:click={() => textToSpeech("Go")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Go</h3>
          <Icon icon="simple-icons:go" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Home")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Home</h3>
          <Icon icon="material-symbols:home" class="w-10 h-10" />
        </div>

      </td>
      <td>
        <div on:click={() => textToSpeech("Shirt")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Shirt</h3>
          <Icon icon="tabler:shirt" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Hat")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Hat</h3>
          <Icon icon="mingcute:hat-fill" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Pants")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Pants</h3>
          <Icon icon="ph:pants" class="w-10 h-10" />
        </div>

      </td>

      <td>
        <div on:click={() => textToSpeech("Case")} class="flex flex-col items-center justify-center">
          <h3 class="text-center text-lg">Case</h3>
          <Icon icon="solar:case-bold" class="w-10 h-10" />
        </div>

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
    padding: 5px;
  }
</style>
