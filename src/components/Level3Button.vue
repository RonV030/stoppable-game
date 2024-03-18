<template>
    <button class="level3-button" @click="handleClick">
      <img v-if="isImage" :src="text" alt="Button Image" />
      <img v-else :src="text" alt="Button GIF" />
    </button>
  </template>
  
  <script>
  export default {
    props: {
      text: {
        type: String,
        required: true
      }
    },
    computed: {
      // Determine if the text is an image or a GIF
      isImage() {
        return /\.(png|jpe?g|gif)$/i.test(this.text);
      }
    },
    methods: {
      handleClick() {
        // Handle button click event here
        console.log("Button clicked!");
      }
    }
  };
  </script>
  
  <style scoped>
  .level3-button {
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
  }
  </style>
  