<script lang="ts">
  let isRecording = false;
  let mediaRecorder: MediaRecorder | null = null;
  let audioChunks: BlobPart[] = [];

  const toggleRecording = async () => {
    if (!isRecording) {
      const startRecording = async () => {
        if (!navigator.mediaDevices) {
          console.error("Media Devices API not supported in your browser.");
          return;
        }

        try {
          const stream = await navigator.mediaDevices.getUserMedia({
            audio: true,
          });
          mediaRecorder = new MediaRecorder(stream);
          mediaRecorder.ondataavailable = (event) => {
            audioChunks.push(event.data);
          };
          mediaRecorder.onstop = async () => {
            const audioBlob = new Blob(audioChunks, { type: "audio/wav" });
            audioChunks = [];

            // Handle the audioBlob here - like sending it to a server for processing
            // This part depends on how you've set up your backend or the service you're using
          };
          mediaRecorder.start();
        } catch (error) {
          console.error("Error accessing media devices:", error);
        }
      };
      console.log("isRecording = true");
      isRecording = true;
    } else {
      const stopRecording = () => {
        if (mediaRecorder) {
          mediaRecorder.stop();
        }
      };
      console.log("isRecording = false");
      isRecording = false;
    }
  };
</script>

<div class="container">
  <button on:click={toggleRecording} class="record-button">
    {#if isRecording}
      <div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="3em"
          height="3em"
          viewBox="0 0 24 24"
          ><path
            fill="currentColor"
            d="M12 14q-1.25 0-2.125-.875T9 11V5q0-1.25.875-2.125T12 2q1.25 0 2.125.875T15 5v6q0 1.25-.875 2.125T12 14m-1 7v-3.075q-2.6-.35-4.3-2.325T5 11h2q0 2.075 1.463 3.538T12 16q2.075 0 3.538-1.463T17 11h2q0 2.625-1.7 4.6T13 17.925V21z"
          /></svg
        >
        Stop
      </div>
    {:else}
      <div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="3em"
          height="3em"
          viewBox="0 0 12 12"
          ><path
            fill="currentColor"
            d="M1.854 1.146a.5.5 0 1 0-.708.708L4 4.707V5.5a2 2 0 0 0 2.676 1.883l.755.755A3 3 0 0 1 3 5.5a.5.5 0 1 0-1.001 0a4 4 0 0 0 3.5 3.97v1.03a.5.5 0 1 0 1 0V9.47a3.976 3.976 0 0 0 1.66-.603l1.986 1.987a.5.5 0 0 0 .708-.708zM9.52 7.4l-.75-.75A2.99 2.99 0 0 0 9 5.5a.5.5 0 1 1 1 0c0 .688-.173 1.335-.479 1.9M7.97 5.849L4.216 2.095A2 2 0 0 1 8 3v2.5c0 .119-.01.235-.03.349"
          /></svg
        > Start
      </div>
    {/if}
  </button>
</div>

<style>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 70vh;
  }

  .record-button {
    border-radius: 50%;
    width: 150px;
    height: 150px;
    padding: 0;
    border: none;
    background-color: #1f3a4c;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .icon {
    width: 24px;
    height: 24px;
    fill: currentColor;
  }
</style>
