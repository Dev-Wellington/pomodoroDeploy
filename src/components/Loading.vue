<template>
  <div id="loading" v-if="isLoading">
    <div class="loading">
      <div v-for="i in 8" :key="i" class="loading-bar"></div>
    </div>
  </div>
  <div v-else>
    <slot name="content"></slot>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const isLoading = ref(true);

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false;
  }, 4000);
});
</script>

<style scoped>
#loading {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
 
  display: flex;
  justify-content: center;
  align-items: center;
}

.loading {
  height: 50px;
  display: flex;
  align-items: center;
}

.loading-bar {
  width: 6px;
  height: 0px;
  background: #0f1729;
  margin: 0 3px;
  border-radius: 10px;
  animation: loading 1.2s infinite;
}

.loading-bar:nth-child(2n){
  animation-delay: 0.15s;
}
.loading-bar:nth-child(3n){
  animation-delay: 0.3s;
}
.loading-bar:nth-child(4n){
  animation-delay: 0.45s;
}
.loading-bar:nth-child(5n){
  animation-delay: 0.6s;
}
.loading-bar:nth-child(6n){
  animation-delay: 0.75s;
}
.loading-bar:nth-child(7n){
  animation-delay: 0.9s;
}
.loading-bar:nth-child(8n){
  animation-delay: 1.05s;
}


@keyframes loading {
  0% {
    height: 0;
  }
  50% {
    height: 50px;
  }
  100% {
    height: 0;
  }
}
</style>
