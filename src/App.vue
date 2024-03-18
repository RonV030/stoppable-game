<template>
    <div>
        <game-start v-if="currentLevel === 0" @restart="restartGame"></game-start>
        <game-over v-if="lives === 0" @restart="restartGame"></game-over>
        <level-one v-if="currentLevel === 1 && lives > 0" :lives="lives" @correctAnswer="advanceLevel" @loseLife="loseLife"></level-one>
        <level-two v-if="currentLevel === 2 && lives > 0" :lives="lives" @correctAnswer="advanceLevel" @loseLife="loseLife"></level-two>
        <level-three v-if="currentLevel === 3 && lives > 0" :lives="lives" @correctAnswer="advanceLevel" @loseLife="loseLife"></level-three>
    </div>
</template>

<script>
import gameStart from './components/GameStart.vue';
import gameOver from './components/GameOver.vue';
import levelOne from './components/LevelOne.vue';
import levelTwo from './components/LevelTwo.vue';
import levelThree from './components/LevelThree.vue';

export default {
    components: {
        levelOne,
        levelTwo,
        levelThree,
        gameOver,
        gameStart
    },
    data() {
        return {
            currentLevel: 0,
            lives: 3,
        };
    },
    methods: {
        advanceLevel() {
            if (this.currentLevel === 3) {
                window.location.href = 'https://myportal.telekom.de/';
            }
            this.currentLevel++;
        },
        loseLife() {
            if (this.lives > 0) {
                this.lives--;
            }
        },
        restartGame() {
            this.currentLevel = 1;
            this.lives = 3;
        },
        disableScrolling() {
            document.body.classList.add('no-scroll');
        },
        enableScrolling() {
            document.body.classList.remove('no-scroll');
        }
    },
    mounted() {
        this.disableScrolling();
    },

    beforeUnmount() {
        this.enableScrolling();
    }
};
</script>
<style>
.no-scroll {
  overflow: hidden;
}
</style>
