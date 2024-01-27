<script lang="ts">
    import { onMount } from 'svelte';
    import RecordRTC from 'recordrtc';
  
    let audioRecorder;
    let isRecording = false;
    let audioClips = [];
  
    async function recordAudio() {
      if (!isRecording) {
        const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
        audioRecorder = RecordRTC(stream, { type: 'audio' });
        audioRecorder.startRecording();
        isRecording = true;
      } else {
        audioRecorder.stopRecording(async () => {
          const blob = audioRecorder.getBlob();
          // Save the blob to IndexedDB
          // You need to implement the saveToIndexedDB function
          await saveToIndexedDB(blob);
          audioClips = [...audioClips, blob];
          isRecording = false;
        });
      }
    }
  </script>
  
  <div>
    <h1 class="font-semibold text-4xl">Settings</h1>
    <p>Add words to your dictionary to improve your experience.</p>
    <button on:click={recordAudio}>{isRecording ? 'Stop Recording' : 'Start Recording'}</button>
    {#each audioClips as audioClip, i}
      <audio controls src={URL.createObjectURL(audioClip)}>Audio Clip {i + 1}</audio>
    {/each}
  </div>