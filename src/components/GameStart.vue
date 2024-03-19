<template>
  <div class="game-start">
    <h1>Are you worthy?</h1>
    <button ref="button" @click="handleButtonClick">Play</button>
  </div>
</template>

<script>
export default {
  name: 'GameStart',
  data() {
    return {
      clickCount: 0
    };
  },
  methods: {
    handleButtonClick() {
      if (this.clickCount === 0) {
        this.switchPosition();
      } else if (this.clickCount === 1) {
        this.restartGame();
      }
    },
    switchPosition() {
      const button = this.$refs.button;
      if (button) {
        for (let i = 0; i < 3; i++) {
          setTimeout(() => {
            const randomX = Math.random() * (window.innerWidth - button.offsetWidth);
            const randomY = Math.random() * (window.innerHeight - button.offsetHeight);
            button.style.transform = `translateX(${randomX}px) translateY(${randomY}px)`;
          }, i * 200);
        }
        this.clickCount++;
      }
    },
    restartGame() {
      this.$emit('restart');
      // Reset button position after restarting the game
      const button = this.$refs.button;
      if (button) {
        button.style.transform = '';
      }
      this.clickCount = 0; // Reset click count for subsequent clicks
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
  transition: transform 0.5s ease; /* Add smooth transition for button position change */
}
</style>
