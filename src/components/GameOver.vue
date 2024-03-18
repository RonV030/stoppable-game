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
  /* Styles for your game over screen */
}
</style>

