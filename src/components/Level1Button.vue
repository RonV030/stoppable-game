<template>
    <div class="level1-button">
      <button
        class="custom-button"
        @mouseenter="swapText"
        @mouseleave="resetText"
        @click="handleClick"
      >
        {{ buttonText }}
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      text: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        buttonText: this.text // Use the provided text prop
      };
    },
    methods: {
      swapText() {
        // Swap text with the button next to it clockwise
        const buttons = ['5', '42', '0', '1']; // Update the array to match the order of your buttons
        const currentIndex = buttons.indexOf(this.buttonText);
        const nextIndex = (currentIndex + 1) % buttons.length;
        this.buttonText = buttons[nextIndex];
      },
      resetText() {
        // Reset text to initial state when mouse leaves
        this.buttonText = this.text;
      },
      handleClick() {
      // Handle button click event
      console.log('Button clicked:', this.buttonText);
    }
    }
  };
  </script>
  
  <style scoped>
  .custom-button {
    padding: 10px 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .custom-button:hover {
    background-color: #45a049;
  }
  </style>
  
  