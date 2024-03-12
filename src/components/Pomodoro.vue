<script setup>
import { ref } from "vue";
import alert from '.././assets/alert.mp3';

const timer = ref("25:00");
const timerBreak = ref("05:00");
const longTimerBreak = ref("15:00");
const startStop = ref("Start");
const countBreak = ref(0);

let intervalId;
let isBreakTime = false;

const playAlert = () => {
  let audio = new Audio(alert);

  for (let i = 0; i < 3; i++) {
    setTimeout(() => {
      audio.play();
    }, i * 1000);
  }
}
const startTimerStopTimer = () => {
  if (startStop.value === "Start") {
    startTimer();
    startStop.value = "Stop";
  } else {
    stopTimer();
    startStop.value = "Start";
  }
};

const startTimer = () => {
  const [minutes, seconds] = timer.value.split(":").map(Number);
  let totalTime = minutes * 60 + seconds;

  intervalId = setInterval(() => {
    totalTime--;

    if (totalTime <= 0) {
      playAlert();
      clearInterval(intervalId);
      if (isBreakTime) {
        timer.value = "25:00";
      } else {
        timer.value = timerBreak.value;
        countBreak.value++;

        //quando as duas pausas de cinco minutos forem ativados , o longTimerBreak será ativado
        if (countBreak.value === 2) {
          timer.value = longTimerBreak.value;
          countBreak.value = 0;
          //console.log("long break está funcionando!");
        }
      }
      isBreakTime = !isBreakTime;
      startTimerStopTimer();
      return;
    }

    const newMinutes = Math.floor(totalTime / 60);
    const newSeconds = totalTime % 60;
    timer.value = `${String(newMinutes).padStart(2, "0")}:${String(
      newSeconds
    ).padStart(2, "0")}`;
  }, 1000);
};

const stopTimer = () => {
  clearInterval(intervalId);
};

const resetTimer = () => {
  timer.value = "25:00";
  stopTimer();
  startStop.value = "Start";
};
</script>

<template>
  <div class="timer-pomodoro">
    <h2>{{ timer }}</h2>
    <div class="buttons">
      <button class="timer-button" @click="startTimerStopTimer">
        {{ startStop }}
      </button>
      <button class="reload-button" @click="resetTimer">
        <img
          src="../assets/reload.svg"
          alt="imagem de uma seta circular com a ponta para a esquerda"
        />
      </button>
     
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.timer-pomodoro {
  color: #0f1729;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 72px;
}
h2 {
  font-size: 128px;
  margin: 0;
  font-family: sans-serif;
}
.buttons {
  display: flex;
 width: 300px;
  justify-content: space-between;
}
.timer-button {
  height: 64px;
  width: 128px;
  padding: 10px 20px;
  border-radius: 5px;
  border: none;
  background-color: #f2f2f2;
  cursor: pointer;
  color: #0f1729;
}
.timer-button:hover {
  background-color: #e6e6e6;
}
.timer-button:active {
  background-color: #f2f2f2;
}
.timer-button {
  font-size: 18px;
  font-weight: 800;
}
.reload-button {
  background-color: transparent;
  border: none;
  cursor: pointer;
}
.reload-button:hover {
  filter: drop-shadow(0 0 5px #0f1729);
}
.reload-button:active {
  filter: drop-shadow(0 0 5px #e6e6e6);
}

@media screen and (min-width: 767px) and (max-width: 1023px) {
  h2{
    font-size: 160px;
    
  }
  .buttons {
    width: 400px;
  }
  .timer-button {
    height: 100px;
    width: 200px;
    font-size: 32px;
  }
}
@media screen and (min-width: 320px) and (max-width: 766px) {
  h2{
    font-size: 120px;

  }
  .buttons {
    width: 300px;
  }
}
</style>
