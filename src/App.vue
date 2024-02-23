<script setup>
import Pomodoro from "./components/Pomodoro.vue";
import Cabecalho from "./components/Cabecalho.vue";
</script>

<template>
  <header>
    <Cabecalho> </Cabecalho>
  </header>
  <main>
    <Pomodoro></Pomodoro>
  </main>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
