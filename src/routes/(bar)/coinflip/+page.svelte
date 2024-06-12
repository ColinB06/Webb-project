<!-- CoinFlip.svelte -->

<script>
  let result = '';
  let flipping = false;
  let coinSide = 'white'; 
  const minFlips = 10;
  async function flipCoin() {
    

   

    const randomNumber = Math.random()*10 + minFlips;
    for (let i = 0;i<randomNumber;i++){
      flipping = !flipping

    
    await new Promise((r)=>setTimeout(r, 250))
  
    }
  }
</script>

<style>
  main {
    margin: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 90vh;
    width: 50vw;
    font-family: Arial, sans-serif;
    background-color: #333;
    border-radius: 10px;
    margin-top: 10px;
    scale: 1;
  }

  h1 {
    font-size: 2rem;
    margin-bottom: 20px;
    color: #ffffff; 
    text-align: center;
  }

  p {
    font-size: 1.2rem;
    margin-bottom: 20px;
    color: #ffffff; 
  }

  button {
    padding: 12px 24px;
    font-size: 1.2rem;
    background-color: #007bff; 
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button:hover {
    background-color: #0056b3; 
  }

  #result {
    font-size: 1.5rem;
    font-weight: bold;
    color: #ffffff; 
    margin-top: 20px;
  }

  
  @keyframes flip-front {
    0% {
      transform: rotateY(0deg);
    }
    25% {
      transform: rotateY(45deg);
    }
    50% {
      transform: rotateY(90deg);
    }
    75% {
      transform: rotateY(135deg);
    }
    100% {
      transform: rotateY(180deg);
   
    }
  }

  
  @keyframes flip-back {
    0% {
      transform: rotateY(180deg);
    }
    50% {
      transform: rotateY(90deg);
    }
    100% {
      transform: rotateY(0deg);
   
    }
  }


  .coin-a-front {
    animation: flip-front 250ms forwards; 
  }

  
  .coin-b-back {
    animation: flip-back 250ms forwards; 
  }


  .coin-a-back {
    animation: flip-back 250ms forwards; 
  }

  
  .coin-b-front {
    animation: flip-front 250ms forwards; 
  }



  .coin {
    width: 125px; 
    height: 125px;
    background-size: cover;
    position: relative;
  }

  .side{
    backface-visibility: hidden;  
    height: 100%;
    width: 100%;
    border-radius: 50%;
    position: absolute;
  }


  .coin-a{
    background-image: url(heads-removebg-preview.png);
    background-size: contain;
    background-position: center;
    transform: rotateY('0deg');

  }
  .coin-b{
    background-image: url(tails-removebg-preview.png);
    background-size:contain;
    background-position: center;
    transform: rotateY('180deg');
  }


</style>

<main>
    <h1>Coin Flip Game</h1>
    <p>Click the button to flip the coin:</p>
    <button on:click={flipCoin}>Flip Coin</button>
    <div class="coin"  >
      <div class="side coin-a" class:coin-a-front={flipping}  class:coin-a-back={!flipping} > </div>
      <div class="side coin-b" class:coin-b-back={flipping} class:coin-b-front={!flipping} > </div>

    </div>

    {#if result && !flipping}
      <p id="result">{result}</p>
    {/if}
    
</main>
