<template>
  <!-- child -->
  <div class="player">
    <h2>{{ name }}</h2>

    <!-- score from a prop -->
    <div class="score">{{ score }}</div>

    <!-- emit an event to parent when click-->
    <button @click="$emit('add-point')" :disabled="disabled">+1</button>
  </div>
</template>

<script>
export default {
  name: "PlayerPanel",
  props: {
    name: { type: String, required: true },
    score: { type: Number, required: true },
    disabled: { type: Boolean, default: false },
  },

  emits: ["add-point"],
}
</script>

<style scoped>
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

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>