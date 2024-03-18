<template>
    <div class="quiz-level">
        <div class="question" v-html="currentQuestion.text"></div>
        <div class="answers">
            <button v-for="(answer, index) in currentQuestion.answers" :key="index" @click="selectAnswer(answer)">
                <img :src="answer.imageURL" :alt="answer.altImage">
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
                text: "Wer wurde getötet: Valeria <br> Wer hat sie gefunden: SorOwOwski",
                answers: [
                    { imageURL: require('../assets/wideole.jpg'), altImage: "Ole", isCorrect: false },
                    { imageURL: require('../assets/widelobster.jpg'), altImage: "Lobster", isCorrect: false },
                    { imageURL: require('../assets/meowboom.gif'), altImage: "Meowboom", isCorrect: true },
                    { imageURL: require('../assets/lucasspiegel.jpg'), altImage: "Lucas", isCorrect: false },
                ],
            },
        };
    },
    methods: {
        selectAnswer(answer) {
            if (answer.isCorrect) {
                // Correct answer logic
                console.log("...")
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

.answers img {
  width: 12vw;
  height: auto;
  display: block;
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

