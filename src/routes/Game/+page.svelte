<script>
  import { sentences } from "../../components/text";

  let currentSentence = 0;
  let typedText = "";
  let result = "";
  let charactersPerMinute = 0;
  let timer = 0;
  let gameRunning = false;
  let markedSentence = [];

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

  #wpm {
    color: #fff;
    margin: 0px;
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
    /* background: linear-gradient(60deg, #f79533, #f37055, #ef4e7b, #a166ab, #5073b8, #1098ad, #07b39b, #6fba82); */
    /* margin-left: auto;
    margin-right: auto; */
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

  <div class="button-game-restart">
    <a class="btn2" on:click={startGame}>
      <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="45" height="45" viewBox="0,0,256,256">
        <g fill="#ffffff" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><g transform="scale(4,4)"><path d="M58,32c0,14.359 -11.641,26 -26,26c-14.359,0 -26,-11.641 -26,-26c0,-14.359 11.641,-26 26,-26c14.359,0 26,11.641 26,26zM45.581,23.785c-1.845,-2.961 -4.678,-5.273 -7.941,-6.478l-1.404,3.746c2.416,0.931 4.501,2.685 5.835,4.888c1.348,2.2 1.873,4.846 1.57,7.394c-0.305,2.544 -1.501,4.95 -3.319,6.747c-1.814,1.799 -4.221,2.973 -6.745,3.261c-2.532,0.311 -5.136,-0.242 -7.295,-1.55c-2.165,-1.297 -3.882,-3.329 -4.769,-5.669c-0.903,-2.326 -0.991,-4.98 -0.245,-7.35c0.48,-1.56 1.321,-3.001 2.415,-4.212l3.145,3.493l2.75,-12.047l-12.281,1.462l3.057,3.395c-1.732,1.844 -3.042,4.08 -3.751,6.511c-1.017,3.433 -0.833,7.176 0.502,10.485c1.318,3.313 3.775,6.125 6.837,7.899c3.059,1.793 6.717,2.5 10.2,2.024c3.501,-0.449 6.815,-2.125 9.27,-4.632c2.466,-2.498 4.068,-5.84 4.438,-9.33c0.376,-3.469 -0.404,-7.08 -2.269,-10.037z"></path></g></g>
        </svg>
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
      <input type="text" bind:value={typedText} on:input={checkInput} placeholder="Enter your text here..." />
    </div>

   <div class="feedback">
    
    <div>
      <button class="btn1-start" on:click={startGame}>START</button>
    </div>

    <div class="result-game">
      <p id="result">{result}</p>
      <p id="charactersPerMinute">CPM: {charactersPerMinute}</p>
      <p id="timer">Time left: {Math.floor(timer / 60)}:{timer % 60}</p>
      <p id="difficulty">[{difficulty}]</p>
    </div>
    
  </div>

  <div class="button-game">
    <button style="background: linear-gradient(60deg, #6fba82, #6fba82); color:white" class="btn1-op" on:click={() => difficulty = "Easy"} disabled={gameRunning}>Easy</button>
    <button style="background: linear-gradient(60deg, #1098ad, #1098ad); color:white" class="btn1-op" on:click={() => difficulty = "Normal"} disabled={gameRunning}>Normal</button>
    <button style="background: linear-gradient(60deg, #ef4e7b, #ef4e7b); color:white" class="btn1-op" on:click={() => difficulty = "Hard"} disabled={gameRunning}>Hard</button>
  </div>
</div>

</main>

