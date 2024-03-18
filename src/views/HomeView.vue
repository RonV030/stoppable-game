<template>
  <div class="home">
    <answer_button @click="handleClick">Hover me!</answer_button>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import answer_button from '@/components/answer_button.vue';

@Options({
  components: {
    HelloWorld,
  },
})
export default class HomeView extends Vue {}
</script>
