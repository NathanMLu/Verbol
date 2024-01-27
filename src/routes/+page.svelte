<script lang="ts">
  import AudioRecorder from "../components/AudioRecorder.svelte";
  import { predict } from "../helper/prediction";

  console.log(predict("hello"));

</script>

<svelte:head>
  <title>Verbol</title>
</svelte:head>

<div>
  <form action="" method="">
    <AudioRecorder />
  </form>
</div>

<style>
</style>
