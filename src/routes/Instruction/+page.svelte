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

  
</style>

<main>
    <h2>.1</h2>
    <div class="img-tuto"><img src={instructionicon} alt=""></div>
    <div class="button">
        <a href="/"><button style="cursor: pointer;" class="btn1">BACK</button></a>
    </div>
</main>