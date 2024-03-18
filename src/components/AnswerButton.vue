<template>
    <button
      class="answer-button"
      :class="{ 'hovered': isHovered }"
      @mouseover="isHovered = true"
      @mouseleave="isHovered = false"
      @click="handleClick"
    >
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isHovered: false
      };
    },
    methods: {
      handleClick() {
        // Handle button click event
      }
    }
  };
  </script>
  
  <style>
  .answer-button {
    /* Define your button styles */
    padding: 10px 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
    font-family: inherit;
    font-size: inherit;
    font-weight: bold;
  }
  
  .answer-button.hovered {
    background-color: #45a049;
  }
  </style>  