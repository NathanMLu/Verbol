<script lang="ts">
  import { onMount } from "svelte";
  // import { ChatGPTAPI } from 'chatgpt'

  let isRecording = false;
  let mediaRecorder: MediaRecorder | null = null;
  let audioChunks: BlobPart[] = [];
  let recognition: any;
  let finalTranscript = "";
  let interimTranscript = "";
  let silenceTimer: any;
  let lastTranscript = "";
  let gptResponse = "";

  const maxTextLength = 300;

  function truncateText(text: string) {
    if (text.length > maxTextLength) {
      return text.substring(text.length - maxTextLength, text.length);
    }
    return text;
  }

  const textToSpeech = () => {
    const lastSentence = finalTranscript.split(".").pop();
    const msg = new SpeechSynthesisUtterance(lastSentence);
    window.speechSynthesis.speak(msg);
  };

  onMount(() => {
    if ("webkitSpeechRecognition" in window) {
      recognition = new (window as any).webkitSpeechRecognition();
      recognition.continuous = true;
      recognition.interimResults = true;

      recognition.onresult = (event: any) => {
        let newInterimTranscript = "";

        for (let i = event.resultIndex; i < event.results.length; ++i) {
          if (event.results[i].isFinal) {
            finalTranscript += event.results[i][0].transcript + " ";
          } else {
            newInterimTranscript += event.results[i][0].transcript;
          }
        }

        // Update the interim transcript only with new data
        interimTranscript = newInterimTranscript;
        console.log("Final:", finalTranscript); // For debugging
        console.log("Interim:", interimTranscript); // For debugging

        resetSilenceTimer(); // Reset the timer on every speech input
      };
    }
  });

  function resetSilenceTimer() {
    lastTranscript = finalTranscript + interimTranscript;

    clearTimeout(silenceTimer);
    silenceTimer = setTimeout(() => {
      // Check if currently recording and transcripts have not changed in the last 2 seconds
      if (
        isRecording &&
        lastTranscript === finalTranscript + interimTranscript
      ) {
        pauseRecording();
        callGPTAPI();
        // example();
      }
    }, 2000); // 2 seconds of silence
  }

  function pauseRecording() {
    if (recognition) recognition.stop();
    isRecording = false;    // example();
  }

  function resumeRecording() {
    if (recognition) recognition.start();
    isRecording = true;
  }

  async function callGPTAPI() {
    // example();
    const context = finalTranscript + interimTranscript; // Combine final and interim text
    const nextWords = ["sad"]; // Replace with your own list of words
    const promptText = `Given the conversation: "${context}", predict the next word from the following options. If it doesn't match in the words and you aren't confident, then say none. Only give the word or none, don't give me anything else. The words that can come next are: [${nextWords.join(
      ", "
    )}]`;

    const apiKey = "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"; // Replace with your actual API key
    console.log("Calling GPT API with:", finalTranscript + interimTranscript); // Debugging

    try {
      const response = await fetch(
        "https://api.openai.com/v1/chat/completions",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Authorization: `Bearer ${apiKey}`, // Using the apiKey variable
          },
          body: JSON.stringify({
            // prompt: promptText,
            // max_tokens: 5, // Adjust as needed
            model: "gpt-3.5-turbo",
            messages: [
              {
                "role": "user",
                "content": promptText,
              },
            ]

          }),
        }
      );
      const data = await response.json();
      gptResponse = data.choices[0].message.content;

      if (gptResponse === "none") {
        // If the response is none, then resume recording
        resumeRecording();
        return;
      } else {
        finalTranscript += gptResponse + " ";
        const msg = new SpeechSynthesisUtterance(gptResponse);
        window.speechSynthesis.speak(msg);
      }

      console.log("GPT API response:", gptResponse); // Debugging

      resumeRecording(); // Resume after handling the response
    } catch (error) {
      console.error("Error calling GPT API:", error);
    }
  }

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
      recognition.start();
      console.log("isRecording = true");
      isRecording = true;
    } else {
      const stopRecording = () => {
        if (mediaRecorder) {
          mediaRecorder.stop();
        }
      };
      recognition.stop();
      console.log("isRecording = false");
      isRecording = false;
    }
  };
  
</script>

<div class="container flex-col justify-center">
  <!-- <div class="gpt-response">
    <p>{gptResponse}</p>
  </div> -->
  <div class="h-80 transcript transcript-box mb-8 p-5">
    <p>{finalTranscript}{interimTranscript}</p>
  </div>
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
  <button class="px-4 py-2 verbolize rounded-lg mt-8" on:click={textToSpeech}>
    Verbolize
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

  .transcript {
    margin-top: 20px;
  }

  .transcript-box {
    margin-top: 20px;
    border: 1px solid #ccc;
    padding: 10px;
    overflow-y: auto;
    background-color: white;
    width: 80%;
    max-width: 600px;
  }

  .verbolize {
    border: 2px solid #1f3a4c;
    border-radius: 10px;
    background-color: #1f3a4c;
    color: white;
  }
</style>
