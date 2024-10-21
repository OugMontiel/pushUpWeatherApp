<!-- IconDisplay.vue -->
<template>
    <span class="icon-container">
      <img :src="icon" :alt="description" />
    </span>
  </template>
  
  <script>
  export default {
    props: {
      icon: String,
      description: String,
    },
  };
  </script>
  
  <style scoped>
  .icon-container {
    width: 2em;
    height: 2em;
    border-radius: 50%;
    background-color: var(--white-soft);
  }
  
  .icon-container img {
    width: 100%;
    height: auto;
    object-fit: contain;
  }
  </style>
  