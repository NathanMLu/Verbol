<script lang="ts">
    import { onMount } from 'svelte';
    import RecordRTC from 'recordrtc';
  
    let audioRecorder;
    let isRecording = false;
    let audioClips = [];
  
    
  </script>
  
  <div>
    <h1 class="font-semibold text-4xl">Settings</h1>
    <p>Add words to your dictionary to improve your experience.</p>
    <button on:click={recordAudio}>{isRecording ? 'Stop Recording' : 'Start Recording'}</button>
    {#each audioClips as audioClip, i}
      <audio controls src={URL.createObjectURL(audioClip)}>Audio Clip {i + 1}</audio>
    {/each}
  </div>