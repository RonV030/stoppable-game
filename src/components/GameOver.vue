<template>
  <div class="game-over">
    <h1>Game Over</h1>
    <button @click="restartGame">Play Again</button>
  </div>
</template>

<script>
export default {
  name: 'GameOver',
  methods: {
    restartGame() {
      this.$emit('restart');
    }
  }
};
</script>

<style scoped>
.game-over {
  text-align: center;
}

.game-over h1 {
  font-size: 10vw;
}

.game-over button {
  border: none;
  background-color: transparent;
  padding: 10px;
  cursor: pointer; /* Change the cursor to indicate a clickable item */
  font-size: 5vw;
}
</style>

