<script>
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Londrina+Solid&display=swap');
  
  
  :global(body, html) {
    margin: 0;
    padding: 0;
    user-select: none;
  }

  .button {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    align-content: stretch;
    padding: 20px;
    margin-top: 9vh;
  }
  
  .btn-back{
    margin-top: 50px;
    margin-left: 20px;
    cursor: pointer;
  
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
    background: linear-gradient(to left, rgb(78 15 159), rgb(255 255 255));
    transition: filter 0.4s linear;
    }
    .btn1:hover
    {
    filter: grayscale(50);
    }
  
  .logo {
    display: flex;
    justify-content: center;
    margin: auto;
    padding-top: 50px;
  }
  
  main {
    background-position: center;
    background-repeat: no-repeat;
    height: 100vh;
    background-image: url("../img/bg-gray.png");
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

  </style>

<main class="container">  
  <header class="logo">
        <img src="https://cdn.discordapp.com/attachments/1174150144204230656/1174176221010088087/output-onlinegiftools_4.gif?ex=6566a3d2&is=65542ed2&hm=db80b2cab1fbffa0aa9b87fe6925654d150d0d35c722012ae2498e2aa0978357&" alt="logo" width="400" height="400">
    </header>
        
    <!--  Botões Menu  -->
    <div class="button">
        <a href="../Game"><button class="btn1">PLAY</button></a>
        <a href="../Instruction" ><button class="btn1">HOW TO PLAY</button></a>
        <!-- <a href="../History" ><button class="btn1">HISTORY</button></a> -->
        <a href="../About" ><button class="btn1">ABOUT</button></a>
    </div>
    <div class="credits">Developed by: MangO-Lab</div>
</main>