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
                text: "Wie viele Studienbegleiter braucht man, um eine Glühbirne zu wechseln?",
                answers: [
                    { text: "0", isCorrect: false },
                    { text: "1", isCorrect: false },
                    { text: "5", isCorrect: true },
                    { text: "42", isCorrect: true },
                ],
            },
        };
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

