<template>
    <button class="level2-button" @click="handleClick">
      <span v-html="emoji"></span>
    </button>
  </template>
  
  <script>
  export default {
    name: 'Level2Button',
    props: {
      emoji: {
        type: String,
        required: true
      }
    },
    methods: {
      handleClick() {
        this.$emit('click');
      }
    }
  }
  </script>
  
  <style scoped>
  .level2-button {
    padding: 10px 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .level2-button:hover {
    background-color: #45a049;
  }
  </style>
  