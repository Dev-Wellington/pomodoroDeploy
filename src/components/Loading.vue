<template>
    <div  class="loading-container"  >
      <div class="loading"></div>
    </div>
  </template>
  
  <script>
 
  </script>
  
  <style scoped>
  .loading-container {
    width: 100%;
    min-height: 90vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-y: hidden;
  }
  
  .loading {
    width: 100px;
    height: 100px;
    background-color: transparent;
    display: block;
    border: 12px solid #0F1729;
    border-top: 12px solid #f2f2f2;
    border-radius: 50%;
    animation: loading 2s linear infinite;
    overflow-y: hidden;
  }
  
  @keyframes loading {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
  </style>
  