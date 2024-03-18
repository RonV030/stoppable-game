<template>
    <button class="tiger-button" @click="handleClick">
      <span v-html="emoji"></span>
    </button>
  </template>
  
  <script>
  export default {
    name: 'TigerButton',
    props: {
      emoji: {
        type: String,
        default: '🐅'
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
  .tiger-button {
    font-size: 3rem; /* Adjust the size as needed */
    padding: 20px 40px; /* Increased padding for larger size */
    background-color: #4CAF50; /* Green color */
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .tiger-button:hover {
    background-color: #45a049; /* Darker green color on hover */
  }
  </style>
  