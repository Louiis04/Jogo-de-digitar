<style>

.card {

    width: 250px;
    border: 1px solid #ddd;
    border-radius: 8px;
    margin: 36px;
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
}

.card-content {
    padding: 16px;
    text-align: center;
    background-color: white;
    flex: 1;
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

</style>

<div class="card">
    <img src="https://cdn.discordapp.com/attachments/1147527897788186695/1174126423628333056/vinicius.jpg?ex=65667571&is=65540071&hm=6256f612a3d860b9b6abe226ecab7a12b380778c411165f4ba31bf920ae1a89e&" alt="Membro1" class="grayscale">
    <div class="card-content">
        <h2>José Vinícius</h2>
        <p>FRONTEND DEVELOPER</p>
        <a href="#" class="social-link">GitHub</a>
    </div>
</div>

<div class="card">
    <img src="https://cdn.discordapp.com/attachments/1147527897788186695/1174126405907390524/luis.jpg?ex=6566756d&is=6554006d&hm=e96ea392937edeb3c5855a22a553e313d448eb4d98ce0baacf87fe85f86ef400&" alt="Membro2" class="grayscale">
    <div class="card-content">
        <h2>Luís Eduardo</h2>
        <p>BACKEND DEVELOPER</p>
        <a href="#" class="social-link">GitHub</a>
    </div>
</div>

<div class="card">
    <img src="https://cdn.discordapp.com/attachments/1147527897788186695/1174126422525227079/victor.jpg?ex=65667571&is=65540071&hm=be884924ff08d2ae0fd77f24d0f6949be7006ae1265e29b11a0d03cafff9539c&" alt="Membro3" class="grayscale">
    <div class="card-content">
        <h2>Victor Gustavo</h2>
        <p>FULLSTACK DEVELOPER</p>
        <a href="#" class="social-link">GitHub</a>
    </div>
</div>


<div class="card">
    <img src="https://cdn.discordapp.com/attachments/1147527897788186695/1174126418523865158/kaue.jpg?ex=65667570&is=65540070&hm=288a4524ff751807e35a911646ab5c07369825256f250431cebc6397f3bf249c&" alt="Membro3" class="grayscale">
    <div class="card-content">
        <h2>Kauê Luí</h2>
        <p>COLLABORATOR</p>
        <a href="#" class="social-link">GitHub</a>
    </div>
</div>

<div class="card">
    <img src="https://cdn.discordapp.com/attachments/1147527897788186695/1174126419907989574/let.png?ex=65667570&is=65540070&hm=0196cb3aa3b67bdff889815ed0b08de21fc39c0bcd799b534506ba23c9e9cd85&" alt="Membro5" class="grayscale">
    <div class="card-content">
        <h2>Maria Leticia</h2>
        <p>COLLABORATOR</p>
        <a href="#" class="social-link">GitHub</a>
    </div>
</div>

<div class="card">
    <img src="https://cdn.discordapp.com/attachments/1147527897788186695/1174126416552538222/isa.png?ex=6566756f&is=6554006f&hm=ed53d0bf5e71e0ba41d31175f4857d0f473a62ae4437387237cc7ecd3531025e&" alt="Membro4" class="grayscale">
    <div class="card-content">
        <h2>Isabelly Arruda</h2>
        <p>COLLABORATOR</p>
        <a href="#" class="social-link">GitHub</a>
    </div>
</div>

<div class="button">
    <a href="/"><button class="btn1">BACK</button></a>
</div>