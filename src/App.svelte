<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
</script>

<main>
  <div class="board">
    {#each board as cell, index}
      <div class={`cell ${cell}`} on:click={() => makeMove(index)}>{cell}</div>
    {/each}
  </div>

  {#if winner}
    <p class="message">
      {#if winner === 'tie'}
        It's a tie!
      {:else}
       {winner} won!
      {/if}
    </p>
  
    <div class="reset" on:click={resetGame}>Reset Game</div>
</main>

<style>
  .board {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  gap: 5px;
  margin-bottom: 20px;
}

.cell {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 4rem;
  font-weight: bold;
  cursor: pointer;
  background-color: #eee;
  transition: background-color 0.2s;
}

.cell:hover {
  background-color: #ddd;
}

.cell.X {
  color: #f00;
}

.cell.O {
  color: #00f;
}

.message {
  font-size: 2rem;
  font-weight: bold;
}

.reset {
  padding: 10px;
  font-size: 1.5rem;
  font-weight: bold;
  cursor: pointer;
  background-color: #eee;
  transition: background-color 0.2s;
}

.reset:hover {
  background-color: #ddd;
}
</style>
