<template>
  <div class="quiz-level">
    <div class="question" v-html="linkedQuestionText"></div>
    <div class="answers">
      <button v-for="(answer, index) in currentQuestion.answers"
                :key="index"
                @click="selectAnswer(answer)"
                :class="{'large-emoji': answer.text === '🐯'}">
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
                textParts: [
                    "Was macht süch",
                    "Tiger",
                    "?"
                ],
                link: "https://de.wikipedia.org/wiki/Tiger",
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
                alert("Eine Aubergeini hat Nikotin in sich, du Tiger.")
                this.$emit('correctAnswer')
            } else {
                this.$emit('lose-life')
            }
        },
    },
    computed: {
        linkedQuestionText() {
            const [preText, linkText, postText] = this.currentQuestion.textParts;
            const link = this.currentQuestion.link;
            return `${preText}<a href="${link}" target="_blank">${linkText}</a>${postText}`;
        }
    },
};
</script>

<style scoped>
.quiz-level {
  position: relative;
  min-height: 100vh;
  text-align: center; /* Center everything in the quiz level */
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
  font-size: 10vw;
}

.answers button.large-emoji {
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

