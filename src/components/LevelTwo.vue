<template>
  <div class="quiz-level">
    <div class="question">{{ currentQuestion.text }}</div>
    <div class="answers">
      <button v-for="(answer, index) in currentQuestion.answers" :key="index" @click="selectAnswer(answer)">
        {{ answer.text }}
      </button>
    </div>
    <div class="lives">Lives: {{ this.lives }}</div>
  </div>
</template>

<script>
export default {
    props: {
        lives: Number
    },
  data() {
    return {
      currentQuestion: {
                text: "Was macht süchTiger?",
                answers: [
                    { text: "🍆", isCorrect: true },
                    { text: "🥒", isCorrect: false },
                    { text: "🐯", isCorrect: false },
                    { text: "🍍", isCorrect: false },
                ],
            },
        };
    },
    methods: {
        selectAnswer(answer) {
            if (answer.isCorrect) {
                // Correct answer logic
                console.log("Eine Aubergini hat Nikotin in sich, du Tiger.")
                this.$emit('correctAnswer')
            } else {
                this.$emit('lose-life')
            }
        },
    },
};
</script>

<style scoped>
.quiz-level {
/* Your styles here */
}
.answers button {
/* Your button styles here */
}
</style>

