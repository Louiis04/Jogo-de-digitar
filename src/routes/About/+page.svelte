<script>
    import joseimg from '../../img/vinicius.jpg';
    import luisimg from '../../img/luis.jpg';
    import victorimg from '../../img/Victor.jpg';
    import kaueimg from '../../img/kaue.jpg';
    import letimg from '../../img/let.png';
    import isaimg from '../../img/isa.png';
    import giticon from '../../img/github_2.png';
    import linkedinicon from '../../img/linkedin.png';
</script>
<style>


@font-face {
  font-family: Poppins;
  src: url(/src/font/BenguiatStd-Book.otf);
}

.devs {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    margin-top: 8vw;
}

.card {
    width: 250px;
    border: 1px solid #ddd;
    border-radius: 8px;
    margin: 25px;
    margin-top: 100px;
    overflow: hidden;
    display: inline-flex;
    flex-direction: column;
    position: relative;
    
}

.card img {
    width: 100%;
    height: 50%;
    object-fit: cover;
    cursor: auto;
}

.card-content {
    padding: 16px;
    text-align: center;
    background-color: white;
    flex: 1;
    font-family: Poppins;

}

.card h2 {
    color: #333;
}

.card p {
    color: #666;
}

.social-link {
    display: block;
    margin-top: 10px;
    text-decoration: none;
    color: #007BFF;
}

.button {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    align-content: stretch;
    padding: 20px;
  }
    #git
    {
        width: 30px;
        cursor: pointer;
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
  
  div.result-game {
    display: flow-root;
    margin-left: auto;
    margin-right: auto;
    margin-top: 30px;
    font-size: 30px;
    background-color: #fff;
    text-align: center;
    border-radius: 40px;
    width: 30%;
  }

  .grayscale{
  cursor: pointer;
  border-radius: 8px;
  filter: grayscale(1);
  transition: .3s linear;
}

.grayscale:hover{
  filter: grayscale(0);
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

<!-- <h1>DEVELOPERS</h1> -->
<div class="devs">
    <!-- <h1>DEVELOPERS</h1> -->
<div class="card">
    <img src={joseimg} alt="Membro1" class="grayscale">
    <div class="card-content">
        <h2>José Vinícius</h2>
        <p>FRONTEND DEVELOPER</p>
        <div class="social-link">
            <a href="https://github.com/Vinnijds">
            <img id="git" src={giticon} alt="GitHub">
        </a>
        </div>
            
    </div>
</div>

<div class="card">
    <img src={luisimg} alt="Membro2" class="grayscale">
    <div class="card-content">
        <h2>Luís Eduardo</h2>
        <p>BACKEND DEVELOPER</p>
        <div class="social-link">
            <a href="https://github.com/Louiis04">
            <img id="git" src={giticon} alt="GitHub"></a>
        </div>
    </div>
</div>

<div class="card">
    <img src={victorimg} alt="Membro3" class="grayscale">
    <div class="card-content">
        <h2>Victor Gustavo</h2>
        <p>FULLSTACK DEVELOPER</p>
        <div class="social-link">
            <a href="https://github.com/victorgustavodev">
            <img id="git" src={giticon} alt="GitHub"></a>
        </div>
    </div>
</div>

<div class="card">
    <img src={kaueimg} alt="Membro3" class="grayscale">
    <div class="card-content">
        <h2>Kauê Luí</h2>
        <p>DESIGNER</p>
        <div class="social-link">
            <a href="https://github.com/KaueLui">
            <img id="git" src={giticon} alt="GitHub"></a>
        </div>
    </div>
</div>

<div class="card">
    <img src={letimg} alt="Membro5" class="grayscale">
    <div class="card-content">
        <h2>Maria Leticia</h2>
        <p>COLLABORATOR</p>
        <div class="social-link">
            <a href="#">
            <img id="git" src={giticon} alt="GitHub"></a>
        </div>
    </div>
</div>

<div class="card">
    <img src={isaimg} alt="Membro4" class="grayscale">
    <div class="card-content">
        <h2>Isabelly Arruda</h2>
        <p>COLLABORATOR</p>
        <div class="social-link">
            <a href="#">
            <img id="git" src={giticon} alt="GitHub"></a>
        </div>
    </div>
</div>
</div>
<div class="button">
    <a href="/"><button style="cursor: pointer;" class="btn1">BACK</button></a>
</div>
