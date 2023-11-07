<script>
  import { onMount } from "svelte";

  const sentences = [
    "The quick brown fox jumps over the lazy dog",
    "The cat sat on the mat",
    "I have a pen",
    "I have an apple",
    "I am going to school",
    "I like to eat pizza",
    "I am a student at the university",
    "I am going to school to learn",
    "I like to play games with friends",
    "A picture is worth a thousand words",
    "The universe is vast and mysterious",
    "The human mind is a powerful tool",
    "The future is full of possibilities",
    "The future is full of possibilities",
    "Peace is the goal of all humanity",
    "Hope is the light that guides us through the darkness",
    "The world is a better place because of you",
    "A picture is worth a thousand words",
    "The road to hell is paved with good intentions",
    "The pen is mightier than the sword",
    "The only thing that is constant is change",
    "The only way to do great work is to love what you do",
    "The journey of a thousand miles begins with a single step."
  ];

  let currentSentence = 0;
  let typedText = "";
  let result = "";
  let wpm = 0;
  let timer = 90; // Tempo em segundos
  let gameRunning = false;

  onMount(() => {
    setNewSentence();

    const timerInterval = setInterval(() => {
      timer--;
      if (timer <= 0) {
        clearInterval(timerInterval);
        endGame(wpm);
      }
    }, 1000);
  });

  function randomizeSentence() {
    let randomIndex;
    do {
      randomIndex = Math.floor(Math.random() * sentences.length);
    } while (randomIndex === currentSentence);
    return randomIndex;
  }

  function setNewSentence() {
    currentSentence = randomizeSentence();
    typedText = "";
    result = "";
    wpm = 0;
  }

  function startGame() {
    if (!gameRunning) {
      setNewSentence();
      timer = 90;
      gameRunning = true;
    }
  }

  function endGame(wpm) {
  if (gameRunning) {
    gameRunning = false;
    typedText = "";
    result = `Congratulations, your WPM is: ${wpm}`;
    timer = 90;
  }
}


function checkInput() {
  if (gameRunning) {
    const characters = typedText.replace(/\s/g, "").length; // Conta o número de caracteres
    const elapsedTime = (90 - timer) / 60;
    wpm = Math.round((characters / 5) / elapsedTime); // Calcula o WPM corretamente

    if (sentences[currentSentence] === typedText) {
      currentSentence++;
      if (currentSentence < sentences.length) {
        setNewSentence();
      } else {
        endGame(wpm);
      }
    }
  }
}
</script>

<style>
  /* Adicionar o css */
</style>

<div>
  <p id="sentence">{sentences[currentSentence]}</p>
  <input type="text" bind:value={typedText} on:input={checkInput} on:keydown={startGame} />
  <p id="result">{result}</p>
  <p id="wpm">WPM: {wpm}</p>
  <p id="timer">Time left: {Math.floor(timer / 60)}:{timer % 60}</p>
  <button on:click={startGame}>Start</button>
</div>
