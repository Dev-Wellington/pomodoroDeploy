<script setup>
</script>

<template>
  <header >
    <h1>Pomodoro</h1>
    <img src="../assets/logo.svg" alt="Imagem ilustrativa de um relógio" />
  </header>
</template>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
  flex-direction: row;
}

h1 {
  font-family: sans-serif;
  color: #0F1729;
}
img{
  height: 32px;
  width: 32px;
}

@media (min-width: 320px) {
  h1 {
    font-size: 48px;
  }

  img {
    height: 48px;
    width: 48px;
  }
  
}

@media (min-width: 767px) {
  h1 {
    font-size: 64px;
  }

  img {
    height: 64px;
    width: 64px;
  }
}



</style>
