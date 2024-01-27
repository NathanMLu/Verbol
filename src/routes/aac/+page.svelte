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

  <table>
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
        <div on:click={() => textToSpeech("More")}>
          <h3 class="text-center text-lg">More</h3>
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
