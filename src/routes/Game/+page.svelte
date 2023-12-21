<script>
  import { sentences } from "../../components/text";
  import audioSrc from './../../audio/endgame1.mp3'

  let currentSentence = 0;
  let typedText = "";
  let result = null;
  let charactersPerMinute = 0;
  let timer = 0;
  let gameRunning = false;
  let markedSentence = [];
  let audio= new Audio(audioSrc);

  let difficulty = "Normal";
  const difficultyTimes = {
    Easy: 60,
    Normal: 45,
    Hard: 30,
  };

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
    charactersPerMinute = 0;
    updateMarkedSentence();
  }

  function startGame() {
    if (!gameRunning) {
      setNewSentence();
      timer = difficultyTimes[difficulty];
      gameRunning = true;

      const timerInterval = setInterval(() => {
        timer--;
        if (timer <= 0) {
          clearInterval(timerInterval);
          endGame(charactersPerMinute);
        }
      }, 1000);
    }
  }

  function endGame() {
    if (gameRunning) {
      gameRunning = false;
      typedText = "";
      result = `Congratulations, your CPM is: ${charactersPerMinute}`;
      timer = difficultyTimes[difficulty];
      audio.play();
      ;
    }
  }

  function updateMarkedSentence() {
    const sentenceArray = sentences[currentSentence].split('');
    const typedArray = typedText.split('');

    markedSentence = sentenceArray.map((char, index) => {
      return {
        char,
        correct: typedArray[index] === char,
        notTyped: typedText && typedArray[index] !== char && !typedArray[index - 1],
        nextToType: index === typedArray.length,
      };
    });
  }

  function checkInput() {
    if (gameRunning) {
      const characters = typedText.replace(/\s/g, "").length;
      const elapsedTime = (difficultyTimes[difficulty] - timer) / 60;
      charactersPerMinute = Math.round((characters) / elapsedTime);

      updateMarkedSentence();

      if (sentences[currentSentence].startsWith(typedText)) {
        if (sentences[currentSentence] === typedText) {
          currentSentence++;
          if (currentSentence < sentences.length) {
            setNewSentence();
          } else {
            endGame();
          }
        }
      }
    }
  }
</script>


<style>

  @font-face{
    font-family: 'NomeDaFonte';
    src: url('../../font/Montserrat-VariableFont_wght.ttf');
    font-weight: normal;
    font-style: normal;
  }

  :global(html) {
    overflow: hidden;
    background-image: url("../../img/bg-gray.png");
    background-repeat: no-repeat;
    margin: -31px;
    background-position: center;
    padding: 0px;
    border: 0px;
    height: 1080px;
  }

  .game {
    font-family: 'Londrina Solid', sans-serif;
    border: 0px;
    text-align: center;
  }

  .sentence {
    font-size: 35px;
    background-color: #fff;
    padding: 3%;
    text-align: center;
    border-radius: 25px;
    width: 77.3%;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    user-select: none;
    
  }

  .dg-imput {
    border: 3px solid #000;
    border-radius: 10px;
    height: 50px;
    line-height: normal;
    color: #282828;
    display: flex;
    width: 83%;
    user-select: auto;
    font-size: 16px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 20px;
  }

  input[type=text] {
    height: 45px;
    width: 99.6%;
    border-radius: 10px;
    font-size: 30px;
    font-family: 'Londrina Solid', sans-serif;
    outline: none;
    border: none;
    padding: 5px;
  }

  #timer {
    color: #fff;
  }

  #difficulty {
    color: #fff;
  }

  p{
    margin: 15px;
  }


  .button-game {
    display : flex;
    flex-direction : row;
    justify-content: center;
    margin-left: 9px;
    margin-top: 20px;
  }

  .button-game-back {
    display: flex;
  }

  .button-game-restart {
    margin-left: 1735px;
    margin-bottom: -80px;
    margin-top: 20px;
  }

  .btn2 {
    margin-top: 30px;
    margin-left: 60px;
    margin-bottom: -70px;
  }

  .btn1{
    border-radius: 20px;
    margin: 5px;
    border: 0px;
    padding: 0px;
    width: 270px;
    height: 70px;
    font-size: 40px;
    font-family: 'Londrina Solid', sans-serif;
    cursor: pointer;
  }


  .btn1-start {
    /* background: linear-gradient(60deg, #000000, #049904, #016105, #000000);
    color: white; */
    border: 0px;
    height: 220px;
    width: 420px;
    font-family: 'Londrina Solid', sans-serif;
    cursor: pointer;
    font-size: 60px;
    border-radius: 20px;
    margin: 20px;
  }

  .btn1-op {
    border-radius: 20px;
    border: 0px;
    width: 280px;
    height: 70px;
    font-size: 40px;
    font-family: 'Londrina Solid', sans-serif;
    cursor: pointer;
    margin-left: 11px;
    margin-top: -23px;
  }

  .result-game {
    background: linear-gradient(60deg, #6fba82, #07b39b, #1098ad, #a166ab, #ef4e7b, #f37055, #f79533);
    margin-top: 20px;
    font-size: 30px;
    border-radius: 20px;
    height: 220px;
    width: 420px;
    filter: blur(0.3px);
    padding: auto;
  }

  .feedback {
    display : flex;
    flex-direction : row;
    justify-content: center;
  
  }

  #result {
    color: black;
    text-shadow: 3px 3px 10px #fff; 
  }

  .correct {
    color: lightgreen;
  }

  .incorrect {
    color: red;
  }

  .notTyped {
    color: #808080;
  }

  .nextToType {
    color: rgb(255, 123, 0);
    text-decoration: underline;
  }

  .timeover{
    display: flow-root;
    margin-top: 260px;
    text-align: center;
    padding: 10px;
  }

  .timeover-text {
    font-family: 'Londrina Solid', sans-serif;
    color: white;
    font-size: 90px;
    margin: 0;
    padding: 0;
  }

  .timeover-text-2 {
    font-family: 'NomeDaFonte', sans-serif;
    color: white;
    font-size: 40px;
    margin: 10px;
  }

  .timeover-text-status {
    font-family: 'NomeDaFonte', sans-serif;
    margin: 10px;
  }

  .text-result {
    margin: 0;
    margin-top: 28px;
    align-items: center;
  }

  .timeover-text-score {
    border-radius: 20px;
    border: 0px;
    width: 270px;
    font-size: 40px;
    align-items: center;
    color: white;
    font-family: 'Londrina Solid', sans-serif;
    background: linear-gradient(60deg, #6fba82, #07b39b, #1098ad, #a166ab, #ef4e7b, #f37055, #f79533);
}

</style>

<!--each Itera sobre cada caractere na sentença marcada, aplicando estilos diferentes com base na correção e status de 
digitação.
o campo de entrada vincula o valor digitado a typedText, ela chama o checkInput.
o result chama o endGame e demonstra o wpm do user
botão é só o start -->

  
  <div class="button-game-back">
    <a href="/" class="btn2">
      <svg xmlns="http://www.w3.org/2000/svg" width="60px" height="60px" viewBox="0 0 24 24" data-name="Layer 1"><path
        d="M20.3284 11.0001V13.0001L7.50011 13.0001L10.7426 16.2426L9.32842 17.6568L3.67157 12L9.32842 6.34314L10.7426 7.75735L7.49988 11.0001L20.3284 11.0001Z"
        fill="white"/></svg>
      </a>
  </div>

{#if !result}
  <div class="game">
    <p class="sentence">       
      {#each markedSentence as { char, correct, notTyped, nextToType }}  
        <span
          class:correct={correct}
          class:incorrect={!correct && !notTyped}
          class:notTyped={notTyped}
          class:nextToType={nextToType}
        >{char}</span>
      {/each}
    </p>

    <div class="dg-imput">
      <input type="text" bind:value={typedText} on:input={checkInput} placeholder="Enter your text here..." />
    </div>

   <div class="feedback">
    <div>
      <button class="btn1-start" on:click={startGame}>START</button>
    </div>

    <div class="result-game">
      <p class="text-result" id="charactersPerMinute">CPM: {charactersPerMinute}</p>
      <p class="text-result" id="timer">Time left: {Math.floor(timer / 60)}:{timer % 60}</p>
      <p class="text-result" id="difficulty">[{difficulty}]</p>
    </div>
  </div>

    <div class="button-game">
      <button style="background: linear-gradient(60deg, #6fba82, #6fba82); color:white" class="btn1-op" on:click={() => difficulty = "Easy"} disabled={gameRunning}>Easy</button>
      <button style="background: linear-gradient(60deg, #1098ad, #1098ad); color:white" class="btn1-op" on:click={() => difficulty = "Normal"} disabled={gameRunning}>Normal</button>
      <button style="background: linear-gradient(60deg, #ef4e7b, #ef4e7b); color:white" class="btn1-op" on:click={() => difficulty = "Hard"} disabled={gameRunning}>Hard</button>
    </div>
  </div>
{:else}
        <div class="timeover">
        <h1 class="timeover-text">YOUR TIME IS OVER!</h1>
        <h1 class="timeover-text-2">Don't be sad this is your score:</h1>
        <button class="timeover-text-score">
          <p id="charactersPerMinute">CPM: {charactersPerMinute}</p>
        </button>
        <p class="timeover-text-status" id="difficulty">You played in mode: {difficulty}</p>
        <p class="timeover-text-status" id="difficulty">Back to menu ⬇️</p>
        <a href="/"><button class="btn1">MENU</button></a>
        </div>
{/if}

