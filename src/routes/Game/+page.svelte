<script>
  import { sentences } from "../../components/text";

  let currentSentence = 0;
  let typedText = "";
  let result = "";
  let charactersPerMinute = 0;
  let timer = 45;
  let gameRunning = false;
  let markedSentence = [];

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
      timer = 45;
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

  function endGame(charactersPerMinute) {
    if (gameRunning) {
      gameRunning = false;
      typedText = "";
      result = `Congratulations, your CPM is: ${charactersPerMinute}`;
      timer = 45;
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
      const elapsedTime = (45 - timer) / 60;
      charactersPerMinute = Math.round((characters) / elapsedTime);

      updateMarkedSentence();

      if (sentences[currentSentence].startsWith(typedText)) {
        if (sentences[currentSentence] === typedText) {
          currentSentence++;
          if (currentSentence < sentences.length) {
            setNewSentence();
          } else {
            endGame(charactersPerMinute);
          }
        }
      }
    }
  }
</script>

<style>
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
    
  }

  .dg-imput {
    border: 3px solid #000;
    border-radius: 10px;
    height: 50px;
    line-height: normal;
    color: #282828;
    display: block;
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

  .result-game {
    background: linear-gradient(60deg, #f79533, #f37055, #ef4e7b, #a166ab, #5073b8, #1098ad, #07b39b, #6fba82);
    display: flow-root;
    margin-left: auto;
    margin-right: auto;
    margin-top: 30px;
    font-size: 30px;
    text-align: center;
    border-radius: 20px;
    width: 28%;
    filter: blur(0.3px);
  }

  #result {
    color: black;
    text-shadow: 3px 3px 10px #fff; 
  }

  #wpm {
    color: #fff;
  }

  #timer {
    color: #fff;
  }

  .button-game {
    display: flex;
    flex-direction: inline;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    align-content: stretch;
    margin-top: 20px;
    
  }

  .button-game-back {
    display: flex;
    
  }

  .btn2{
    margin-top: 60px;
    margin-left: 60px;
    margin-bottom: -70px;
  }

  .btn1 {
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

  .correct {
    color: lightgreen;
  }

  .incorrect {
    color: red;
  }

  .notTyped {
    color: black;
  }

  .nextToType {
    color: rgb(255, 123, 0)
  }
</style>

<!--each Itera sobre cada caractere na sentença marcada, aplicando estilos diferentes com base na correção e status de 
digitação.
o campo de entrada vincula o valor digitado a typedText, ela chama o checkInput.
o result chama o endGame e demonstra o wpm do user
botão é só o start -->

<main>
  
  <div class="button-game-back">
    <a href="/" class="btn2">
      <svg xmlns="http://www.w3.org/2000/svg" width="60px" height="60px" viewBox="0 0 24 24" data-name="Layer 1"><path
        d="M20.3284 11.0001V13.0001L7.50011 13.0001L10.7426 16.2426L9.32842 17.6568L3.67157 12L9.32842 6.34314L10.7426 7.75735L7.49988 11.0001L20.3284 11.0001Z"
        fill="white"/></svg>
      </a>
  </div>

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
      <input type="text" bind:value={typedText} on:input={checkInput} />
    </div>

    <div class="result-game">
      <p id="result">{result}</p>
      <p id="charactersPerMinute">CPM: {charactersPerMinute}</p>
      <p id="timer">Time left: {Math.floor(timer / 60)}:{timer % 60}</p>
    </div>

    <div class="button-game">
      <button class="btn1-start" on:click={startGame}>START</button>
    </div>
  </div>

</main>

