<script>
    import instructionicon from '../../img/instruction.png'
</script>

<style>


.container
{
    display: flex;
    width: 100%;
    height: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

main {
    background-position: center;
    background-repeat: no-repeat;
    height: 100vh;
    background-image: url("../../img/bg-gray.png");
  }
.img-tuto
{
    display: flex;
    justify-content: center;
}

.button 
{
    padding-top: 40px;
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

.credits
  {
    font-family: 'Courier New', Courier, monospace;
    /* text-transform: uppercase; */
    position: fixed;
    right: 20px;
    bottom: 10px;
    color: white;
    font-weight: 700;
  }
  .button-game-back {
    position: fixed;
    top: 15px;
    left: 15px;
  }
  
</style>

<main>
    <div class="button-game-back">
        <a href="/" class="btn2">
          <svg xmlns="http://www.w3.org/2000/svg" width="60px" height="60px" viewBox="0 0 24 24" data-name="Layer 1"><path
            d="M20.3284 11.0001V13.0001L7.50011 13.0001L10.7426 16.2426L9.32842 17.6568L3.67157 12L9.32842 6.34314L10.7426 7.75735L7.49988 11.0001L20.3284 11.0001Z"
            fill="white"/></svg>
          </a>
      </div>
    <div class="container">
    <div class="img-tuto"><img src={instructionicon} alt="instruction" style="height:40vw; width: 80vw;"></div>
</div>
</main>