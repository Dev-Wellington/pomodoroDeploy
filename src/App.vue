<script setup>
import Pomodoro from "./components/Pomodoro.vue";
import Cabecalho from "./components/Cabecalho.vue";
import Task from "./components/tasks/Task.vue";

</script>

<template>
  <header>
    <Cabecalho></Cabecalho>
  </header>
  <main>
    <Pomodoro></Pomodoro>
    <Task></Task>
  </main>
  
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
main{
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  gap:20px;
}
</style>
