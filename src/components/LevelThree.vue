<template>
    <div class="quiz-level">
        <div class="question">{{ currentQuestion.text }}</div>
        <div class="answers">
            <button v-for="(answer, index) in currentQuestion.answers" :key="index" @click="selectAnswer(answer)">
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
                text: "Wer wurde getötet: Valeria \n Wer hat sie gefunden: SorOwOwski",
                answers: [
                    { text: "Ole", isCorrect: false },
                    { text: "Markus", isCorrect: false },
                    { text: "Svenorita", isCorrect: true },
                    { text: "Major Monogram", isCorrect: false },
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
  /* Your styles here */
}
.answers button {
  /* Your button styles here */
}
</style>

