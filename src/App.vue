<!-- src/App.vue -->
<template>
  <!-- UI -->
  <main class="app">
    <h1>Resultattavle</h1>

    <!-- score boxes -->
    <section class="board">
      <div class="player">
        <h2>Player 1</h2>
        <div class="score">{{ player1 }}</div>
        <button @click="addPoint(1)">+1</button>
      </div>

      <div class="player">
        <h2>Player 2</h2>
        <div class="score">{{ player2 }}</div>
        <button @click="addPoint(2)">+1</button>
      </div>
    </section>

    <!-- Status message -->
    <p class="status">{{ statusMessage }}</p>

    <!-- Reset button -->
    <button class="reset" @click="resetGame">Nulstil</button>
  </main>
</template>

<script>
/*
- reactive data (player1, player2)
- methods placeholders (addPoint, resetGame)
*/
export default {
  name: "App",

  data() {
    return {
      player1: 0,
      player2: 0,

      // !add rules
      statusMessage: "Playing…",
    }
  },

  methods: {
    addPoint(playerNumber) {
      // add point
      if (playerNumber === 1) this.player1++
      if (playerNumber === 2) this.player2++
    },

    resetGame() {
      this.player1 = 0
      this.player2 = 0
      this.statusMessage = "Playing…"
    },
  },
}
</script>

<style scoped>
.app {
  max-width: 30%;
  margin: 40px auto;
  padding: 24px;
  background-color: rgb(236, 236, 236);
  border-radius: 16px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.board {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin: 12px 0;
}

.player {
  padding: 16px;
}

.score {
  font-size: 62px;
  font-weight: 700;
  margin: 14px 0;
}

button {
  padding: 10px 14px;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  background-color: rgb(253, 253, 253);
}

.status {
  margin: 12px 0 20px;
  min-height: 24px;
}

.reset {
  margin-top: 6px;
}
</style>