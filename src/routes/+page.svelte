<script lang="ts">
  import AudioRecorder from "../components/AudioRecorder.svelte";
  import { predict } from "../helper/prediction";


</script>

<svelte:head>
  <title>Verbol</title>
</svelte:head>

<h1 class="font-semibold text-4xl">Verbol</h1>
<p>Verbol is a communication tool for people with speech disabilities.</p>

<div>
  <form action="" method="">
    <AudioRecorder />
  </form>
</div>

<style>
</style>
