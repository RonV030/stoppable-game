<template>
    <div class="quiz-level">
        <div class="question" v-html="currentQuestion.text"></div>
        <div class="answers">
            <button v-for="(answer, index) in currentQuestion.answers"
                :key="index"
                @mouseenter="swapText(index)"
                @mouseleave="resetText(index)"
                @click="selectAnswer(answer)">
                {{ answer.text }}
            </button>
        </div>
        <div class="lives">Lives: {{ lives }}</div>
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
                text: "Wie viele Studienbegleiter braucht man,<br> um eine Glühbirne zu wechseln?",
                answers: [
                    { text: "0", isCorrect: false },
                    { text: "1", isCorrect: false },
                    { text: "5", isCorrect: true },
                    { text: "42", isCorrect: false },
                ],
            },
            originalAnswers: [],
        };
    },
    mounted() {
        this.originalAnswers = JSON.parse(JSON.stringify(this.currentQuestion.answers));
    },
    methods: {
        selectAnswer(answer) {
            if (answer.isCorrect) {
                // Correct answer logic
                console.log('Einer*in hälts und die anderen trinken, bis sich alles um sie herum dreht.');
                this.$emit('correctAnswer')
            } else {
                this.$emit('lose-life')
            }
        },
        swapText(index) {
            // Swap text with the next button clockwise
            const nextIndex = (index + 1) % this.currentQuestion.answers.length;
            const temp = this.currentQuestion.answers[index].text;
            this.currentQuestion.answers[index].text = this.currentQuestion.answers[nextIndex].text;
            this.currentQuestion.answers[nextIndex].text = temp;
        },
        resetText(index) {
            // Reset text to initial state when mouse leaves
            this.currentQuestion.answers[index].text = this.originalAnswers[index].text;
        },
    },
};
</script>

<style scoped>
.quiz-level {
  position: relative;
  min-height: 100vh;
  text-align: center;
}

.question {
  font-size: 5vw; /* Make the question text larger */
  margin-bottom: 20px; /* Add space below the question */
  white-space: pre-line;
}

.answers button {
  margin: 5px; /* Add space between buttons */
  border: none;
  background-color: transparent;
  padding: 10px;
  cursor: pointer; /* Change the cursor to indicate a clickable item */
  font-size: 20vw;
}

.lives {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 1vw;
  font-size: 10vw; /* Larger font for lives */
  color: red; /* Change color to red or any color you prefer */
  margin-top: 20px; /* Space above the lives counter */
}
</style>

