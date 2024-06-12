<script>
  import { onMount } from 'svelte';
  

  const cards = [
    { rank: '2', suit: 's', value: 2, image: 'images/2s.jpg' },
    { rank: '3', suit: 's', value: 3, image: 'images/3s.jpg' },
    { rank: '4', suit: 's', value: 4, image: 'images/4s.jpg' },
    { rank: '5', suit: 's', value: 5, image: 'images/5s.jpg' },
    { rank: '6', suit: 's', value: 6, image: 'images/6s.jpg' },
    { rank: '7', suit: 's', value: 7, image: 'images/7s.jpg' },
    { rank: '8', suit: 's', value: 8, image: 'images/8s.jpg' },
    { rank: '9', suit: 's', value: 9, image: 'images/9s.jpg' },
    { rank: '10', suit: 's', value: 10, image: 'images/10s.jpg' },
    { rank: 'J', suit: 's', value: 10, image: 'images/Js.jpg' },
    { rank: 'Q', suit: 's', value: 10, image: 'images/Qs.jpg' },
    { rank: 'K', suit: 's', value: 10, image: 'images/Ks.jpg' },
    { rank: 'A', suit: 's', value: 11, image: 'images/11s.jpg' },
    { rank: '2', suit: 'h', value: 2, image: 'images/2h.jpg' },
    { rank: '3', suit: 'h', value: 3, image: 'images/3h.jpg' },
    { rank: '4', suit: 'h', value: 4, image: 'images/4h.jpg' },
    { rank: '5', suit: 'h', value: 5, image: 'images/5h.jpg' },
    { rank: '6', suit: 'h', value: 6, image: 'images/6h.jpg' },
    { rank: '7', suit: 'h', value: 7, image: 'images/7h.jpg' },
    { rank: '8', suit: 'h', value: 8, image: 'images/8h.jpg' },
    { rank: '9', suit: 'h', value: 9, image: 'images/9h.jpg' },
    { rank: '10', suit: 'h', value: 10, image: 'images/10h.jpg' },
    { rank: 'J', suit: 'h', value: 10, image: 'images/Jh.jpg' },
    { rank: 'Q', suit: 'h', value: 10, image: 'images/Qh.jpg' },
    { rank: 'K', suit: 'h', value: 10, image: 'images/Kh.jpg' },
    { rank: 'A', suit: 'h', value: 11, image: 'images/11h.jpg' },
    { rank: '2', suit: 'd', value: 2, image: 'images/2d.jpg' },
    { rank: '3', suit: 'd', value: 3, image: 'images/3d.jpg' },
    { rank: '4', suit: 'd', value: 4, image: 'images/4d.jpg' },
    { rank: '5', suit: 'd', value: 5, image: 'images/5d.jpg' },
    { rank: '6', suit: 'd', value: 6, image: 'images/6d.jpg' },
    { rank: '7', suit: 'd', value: 7, image: 'images/7d.jpg' },
    { rank: '8', suit: 'd', value: 8, image: 'images/8d.jpg' },
    { rank: '9', suit: 'd', value: 9, image: 'images/9d.jpg' },
    { rank: '10', suit: 'd', value: 10, image: 'images/10d.jpg' },
    { rank: 'J', suit: 'd', value: 10, image: 'images/Jd.jpg' },
    { rank: 'Q', suit: 'd', value: 10, image: 'images/Qd.jpg' },
    { rank: 'K', suit: 'd', value: 10, image: 'images/Kd.jpg' },
    { rank: 'A', suit: 'd', value: 11, image: 'images/11d.jpg' },
    { rank: '2', suit: 'c', value: 2, image: 'images/2c.jpg' },
    { rank: '3', suit: 'c', value: 3, image: 'images/3c.jpg' },
    { rank: '4', suit: 'c', value: 4, image: 'images/4c.jpg' },
    { rank: '5', suit: 'c', value: 5, image: 'images/5c.jpg' },
    { rank: '6', suit: 'c', value: 6, image: 'images/6c.jpg' },
    { rank: '7', suit: 'c', value: 7, image: 'images/7c.jpg' },
    { rank: '8', suit: 'c', value: 8, image: 'images/8c.jpg' },
    { rank: '9', suit: 'c', value: 9, image: 'images/9c.jpg' },
    { rank: '10', suit: 'c', value: 10, image: 'images/10c.jpg' },
    { rank: 'J', suit: 'c', value: 10, image: 'images/Jc.jpg' },
    { rank: 'Q', suit: 'c', value: 10, image: 'images/Qc.jpg' },
    { rank: 'K', suit: 'c', value: 10, image: 'images/Kc.jpg' },
    { rank: 'A', suit: 'c', value: 11, image: 'images/11c.jpg' }
  ];

  let deck = [...cards];
  // @ts-ignore
  let playerHand = [];
  // @ts-ignore
  let dealerHand = [];
  let gameMessage = '';

  
  // @ts-ignore
  function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
    return array;
  }

  
  function drawCard() {
    return deck.pop();
  }

  
  // @ts-ignore
  function calculateHandValue(hand) {
    let value = 0;
    let aceCount = 0;

    // @ts-ignore
    hand.forEach(card => {
      value += card.value;
      if (card.rank === 'A') aceCount++;
    });

    
    while (value > 21 && aceCount > 0) {
      value -= 10;
      aceCount--;
    }

    return value;
  }

  
  function startGame() {
    deck = shuffle([...cards]);
    playerHand = [drawCard(), drawCard()];
    dealerHand = [drawCard(), drawCard()];
    gameMessage = '';
  }

  
  function hit() {
    playerHand.push(drawCard());
    // @ts-ignore
    const playerValue = calculateHandValue(playerHand);
    if (playerValue > 21) {
      gameMessage = 'Player busts!';
      // @ts-ignore
    }      
    playerHand = playerHand;

  }

 
  function stand() {
    // @ts-ignore
    let dealerValue = calculateHandValue(dealerHand);
    while (dealerValue < 17) {
      dealerHand.push(drawCard());
      // @ts-ignore
      dealerValue = calculateHandValue(dealerHand);
      // @ts-ignore
      dealerHand = dealerHand;
    }

    // @ts-ignore
    const playerValue = calculateHandValue(playerHand);

    if (dealerValue > 21 || playerValue > dealerValue) {
      gameMessage = 'Player wins!';
    } else if (playerValue < dealerValue) {
      gameMessage = 'Dealer wins!';
    } else {
      gameMessage = 'Push!';
    }
  }

  onMount(() => {
    startGame();
  });
</script>

<main>
  <h1>Blackjack</h1>
  <div class="hand">
    <h2>Player's Hand</h2>
    <div class="card-container">
      {#each playerHand as card}
        <img src={card.image} alt={card.rank + card.suit} width="100" class="card" />
      {/each}
    </div>
    <p>Total Value: {calculateHandValue(playerHand)}</p> 
    <button on:click={hit} disabled={gameMessage}>Hit</button>
    <button on:click={stand} disabled={gameMessage}>Stand</button>
  </div>

  <div class="hand">
    <h2>Dealer's Hand</h2>
    <div class="card-container">
      {#each dealerHand as card}
        <img src={card.image} alt={card.rank + card.suit} width="100" class="card" />
      {/each}
    </div>
    <p>Total Value: {calculateHandValue(dealerHand)}</p> 
  </div>

  <div>
    <h2>{gameMessage}</h2>
    {#if gameMessage}
      <button on:click={startGame}>New Game</button>
    {/if}
  </div>
</main>

<style>
  main {
    text-align: center;
    margin-top: 50px;
  }
  
  .hand {
    margin-bottom: 20px;
  }
  
  .card-container {
    display: flex;
    justify-content: center;
  }
  
  .card {
    margin: 0 5px;
  }

  button {
    margin: 0 10px;
    padding: 10px 20px;
    font-size: 1rem;
    cursor: pointer;
  }

  button[disabled] {
    opacity: 0.5;
    cursor: not-allowed;
  }
</style>