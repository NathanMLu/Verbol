<script lang="ts">
  import Icon from "@iconify/svelte";
  

  function textToSpeech(name: string) {
    console.log("This has been clicked " + name);

    const msg = new SpeechSynthesisUtterance(name);
    window.speechSynthesis.speak(msg);
    
  }


</script>

<div>
  <h1>AAC Page</h1>
  <p>
    This page holds holds the AAC that allows for people with severe speech
    impediments to communicate.
  </p>
  <Icon icon="" />

  <table class="table-auto">
    <tr>
      <td class="flex flex-col align-middle">
        <div on:click={() => textToSpeech("Eat")}>
          <h3 class="text-center text-lg">Eat</h3>
          <Icon icon="fluent-mdl2:eat-drink" class="w-10 h-10" />
        </div>
      </td>
      <td>
        <div on:click={() => textToSpeech("Bathroom")}>
          <h3 class="text-center text-lg">Bathroom</h3>
          <Icon icon="cbi:roomsbathroom" class="w-10 h-10" />
        </div>
      </td>
      <td>
        <div on:click={() => textToSpeech("Yes")}>
          <h3 class="text-center text-lg">Yes</h3>

          <Icon icon="healthicons:yes-outline" class="w-10 h-10" />
        </div>
      </td>

      <td>
        <div on:click={() => textToSpeech("No")}>
          <h3 class="text-center text-lg">No</h3>
          <Icon icon="dashicons:no" class="w-10 h-10" />
        </div>
      </td>

      <td>
        <div on:click={() => textToSpeech("Out")}>
          <h3 class="text-center text-lg">Out</h3>
          <Icon icon="arcticons:clear-outside" class="w-10 h-10" />
        </div>
      </td>

      <td>
        <div on:click={() => textToSpeech("In")}>
          <h3 class="text-center text-lg">In</h3>
          <Icon icon="ic:outline-expand-less" class="w-10 h-10" />
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
    padding: 8px;
  }
</style>
