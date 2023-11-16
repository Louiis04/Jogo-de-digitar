<script>
  import { onMount } from "svelte";
  import { sentences } from "../../components/text";

  let currentSentence = 0;    //acompanha o texto atual digitado
  let typedText = "";         //armazena o texto digitado pelo user
  let result = "";            //armazena a mensagem de resultado final do jogo
  let wpm = 0;                //palavras por minuto digitada
  let timer = 90;             //contador regressivo
  let gameRunning = false;    //se o jogo está em fucionamento
  let markedSentence = [];    //array que armazena cada letra digitada, e a proxima letra a ser digitada

  onMount(() => {
    setNewSentence();     //inicia o primeiro texto

    const timerInterval = setInterval(() => {       //caso o tempo chegue a zero a função fim de jogo é chamada
      timer--;
      if (timer <= 0) {
        clearInterval(timerInterval);
        endGame(wpm);
      }
    }, 1000);
  });

  function randomizeSentence() {        // randomiza o texto que vai aparecer
    let randomIndex;
    do {
      randomIndex = Math.floor(Math.random() * sentences.length);
    } while (randomIndex === currentSentence);
    return randomIndex;
  }

  function setNewSentence() {                   // caso o usuario termine o texto ele puxa outro texto
    currentSentence = randomizeSentence();
    typedText = "";
    result = "";
    wpm = 0;
    updateMarkedSentence();
  }

  function startGame() {                   //inicia o jogo
    if (!gameRunning) {
      setNewSentence();
      timer = 90;
      gameRunning = true;
    }
  }

  function endGame(wpm) {                  //finaliza o jogo
    if (gameRunning) {
      gameRunning = false;
      typedText = "";
      result = `Congratulations, your WPM is: ${wpm}`;
      timer = 90;
    }
  }

  function updateMarkedSentence() {                           //atualiza o array "markedsentece"
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

  function checkInput() {               // caso o usuario finalize um texto corretamente ele puxa outro texto
    if (gameRunning) {
      const characters = typedText.replace(/\s/g, "").length;
      const elapsedTime = (90 - timer) / 60;
      wpm = Math.round((characters / 5) / elapsedTime);

      updateMarkedSentence();                  // chamada da função do marcador 

      if (sentences[currentSentence].startsWith(typedText)) {
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
  }
  /* each Itera sobre cada caractere na sentença marcada, aplicando estilos diferentes com base na correção e status de 
  digitação.
o campo de entrada vincula o valor digitado a typedText, ela chama o checkInput.
o result chama o endGame e demonstra o wpm do user
botão é só o start*/
</script>

<style>
  :global(html) {
    overflow: hidden;
    background-image: url("https://cdn.discordapp.com/attachments/1147527897788186695/1174171539860631592/Main.png?ex=65669f76&is=65542a76&hm=5fe2e6328fc1e7fac22e1a108a95846c277628ffa9affbce19b894e159e1e697&");
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

<main>
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
      <p id="wpm">WPM: {wpm}</p>
      <p id="timer">Time left: {Math.floor(timer / 60)}:{timer % 60}</p>
    </div>

    <div class="button-game">
      <button class="btn1" on:click={startGame}>START</button>
      <a href="/"><button class="btn1">BACK</button></a>
    </div>
  </div>
</main>

