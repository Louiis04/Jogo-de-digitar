<script>
    import instructionicon from '../../img/instruction.png'
</script>

<style>

.img-tuto
{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.button 
{
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    align-content: stretch;
    padding: 20px;
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
}

.button-game {
    display : flex;
    flex-direction : row;
    justify-content: center;
    margin-left: 9px;
    margin-top: 20px;
  }

  .btn2 {
    margin-top: 30px;
    margin-left: 60px;
    margin-bottom: -70px;
  }

  .button-game-back {
    display: flex;
  }
  
</style>

<div class="button-game-back">
    <a href="/" class="btn2">
      <svg xmlns="http://www.w3.org/2000/svg" width="60px" height="60px" viewBox="0 0 24 24" data-name="Layer 1"><path
        d="M20.3284 11.0001V13.0001L7.50011 13.0001L10.7426 16.2426L9.32842 17.6568L3.67157 12L9.32842 6.34314L10.7426 7.75735L7.49988 11.0001L20.3284 11.0001Z"
        fill="white"/></svg>
      </a>
  </div>

<main>
    <h2>.1</h2>
    <div class="img-tuto"><img src={instructionicon} alt=""></div>
</main>