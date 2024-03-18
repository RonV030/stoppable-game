<template>
  <div class="game-start">
    <h1>Are you worthy?</h1>
    <button @click="restartGame">Play</button>
  </div>
</template>

<script>
export default {
  name: 'GameStart',
  methods: {
    restartGame() {
      this.$emit('restart');
    }
  }
};
</script>

<style scoped>
.game-start {
  text-align: center;
}

.game-start h1 {
  font-size: 10vw;
}

.game-start button {
  border: none;
  background-color: transparent;
  padding: 10px;
  cursor: pointer; /* Change the cursor to indicate a clickable item */
  font-size: 5vw;
}
</style>

