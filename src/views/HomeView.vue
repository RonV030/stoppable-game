<template>
  <div class="home">
    <answer-button @click="handleClick">Hover me!</answer-button>
  </div>
  <div id="app">
    <div class="button-row">
      <Level1Button text="5"/>
      <Level1Button text="42"/>
    </div>
    <div class="button-row">
      <Level1Button text="0"/>
      <Level1Button text="1"/>
    </div>

    <div class="button-row">
      <Level2Button emoji="🍆" @click="handleClick" />
      <Level2Button emoji="🥒" @click="handleClick" />
    </div>
    <div class="button-row">
      <TigerButton emoji="🐅" @click="handleClick" />
      <Level2Button emoji="🍍" @click="handleClick" />
    </div>

    <div class="button-row">
      <Level3Button text="C:\Users\A200162433\OneDrive - Deutsche Telekom AG\Dokumente\Code\stoppable-game\stoppable-game\src\assets\Download.jpg" @click="handleClick" />
      <Level3Button text="🥒" @click="handleClick" />
    </div>
    <div class="button-row">
      <Level3Button text="🐅" @click="handleClick" />
      <Level3Button text="🍍" @click="handleClick" />
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import AnswerButton from '@/components/AnswerButton.vue';
import Level1Button from '@/components/Level1Button.vue';
import Level2Button from '@/components/Level2Button.vue';
import TigerButton from '@/components/TigerButton.vue';
import Level3Button from "@/components/Level3Button.vue";

@Options({
  components: {
    AnswerButton,
    Level1Button,
    Level2Button,
    TigerButton,
    Level3Button,
  },
})
export default class HomeView extends Vue {
  handleClick() {
    // Handle AnswerButton click event
    alert('AnswerButton clicked!');
  }
}
</script>

<style scoped>
/* Your scoped styles for HomeView */
.button-row {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.button-row >>> tiger-button {
  font-size: 3rem;
  padding: 20px 40px;
}

/* Other buttons maintain their default size */
.button-row >>> level2-button {
  font-size: 1rem; /* Default font size */
  padding: 10px 20px; /* Default padding */
}

/* Optional: Adjust the button size and spacing */
.level1-button {
  margin: 5px; /* Adjust the spacing between buttons */
}
</style>
