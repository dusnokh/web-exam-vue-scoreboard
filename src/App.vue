<!-- src/App.vue -->
<template>
  <!-- UI -->
  <main class="app">
    <h1>Resultattavle</h1>

    <!-- score boxes -->
    <section class="board">
      <PlayerPanel
        name="Player 1"
        :score="player1"
        :disabled="gameOver"
        @add-point="addPoint(1)"
      />

      <PlayerPanel
        name="Player 2"
        :score="player2"
        :disabled="gameOver"
        @add-point="addPoint(2)"
      />
    </section>

    <!-- Status message -->
    <p class="status">{{ statusMessage }}</p>

    <!-- Reset button -->
    <button class="reset" @click="resetGame">Nulstil</button>
  </main>
</template>

<script>
import PlayerPanel from "./components/PlayerPanel.vue"
export default {
  name: "App",
  components: { PlayerPanel },

  data() {
    return {
      player1: 0,
      player2: 0,
    }
  },
  computed: {
    isDraw() {
      // Rule for 11:11
      return this.player1 === 11 && this.player2 === 11
    },

    winner() {
      // Rule for 6 points + min 2 difference
      const p1Wins = this.player1 >= 6 && this.player1 - this.player2 >= 2
      const p2Wins = this.player2 >= 6 && this.player2 - this.player1 >= 2

      if (p1Wins) return "Player 1"
      if (p2Wins) return "Player 2"

      // no winner yet
      return null
    },

    gameOver() {
      // endof game in case of winner or draw
      return this.winner !== null || this.isDraw
    },

    statusMessage() {
      if (this.winner) return `Vinder: ${this.winner}`
      if (this.isDraw) return "Uafgjort (11–11). Game over."
      return "Kampen er i gang..."
    },
  },

  methods: {
    addPoint(playerNumber) {
      // stop scoring if game ended
      if (this.gameOver) return

      // add point
      if (playerNumber === 1) this.player1++
      if (playerNumber === 2) this.player2++
    },

    resetGame() {
      this.player1 = 0
      this.player2 = 0
    },
  },
}
</script>

<style scoped>
.app {
  max-width: 420px;
  margin: 40px auto;
  padding: 24px;
  background-color: rgb(236, 236, 236);
  border-radius: 20px;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.08);
  font-family: "Inter", "Segoe UI", -apple-system, BlinkMacSystemFont, sans-serif;
  background: linear-gradient(135deg, #f2f4f8, #e8ecf2);
  margin: 0;
}

.board {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin: 12px 0;
  margin: 16px 0;
}

.status {
  margin: 18px 0 24px;
  min-height: 24px;
}

.reset {
  margin-top: 6px;
}

.reset:hover {
  background-color: rgb(252, 192, 80);
  color: white;
}

button {
  padding: 10px 14px;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  background-color: #fbfcff;
  transition: background-color 0.25s ease, color 0.25s ease;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

</style>