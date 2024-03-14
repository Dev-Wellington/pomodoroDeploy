<template>
  <div class="task-container">
    <div class="show-task">
      <h2>Add Tasks</h2>
      <button @click="showPomoTask" class="btn-show-task">Add Task</button>
    </div>
    <div v-show="showPomoModal" class="add-task">
      <input
        type="text"
        placeholder="Add a task"
        class="input-task"
        v-model.trim="inputTask"
        @keyup.enter="addTask"
      />
      <button :disabled="!inputTask" @click="addTask" class="btn-add-task">
        Add
      </button>
    </div>

    <div v-for="(task, index) in tasks" :key="index" class="task">
      <p class="task-p">{{ task }}</p>
      <button @click="removeTask(index)" class="btn-remove">
        <img src="../../assets/remove.svg" alt="Remove Task" />
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const inputTask = ref("");
const tasks = ref([]); //

const showTaskLocalStorage = () => {
  const storedTasks = localStorage.getItem("tasks");
  if (storedTasks) {
    tasks.value = JSON.parse(storedTasks);
  }
};

onMounted(() => {
  showTaskLocalStorage();
});

const addTask = () => {
  if (inputTask.value.trim() !== "") {
    const taskExists = tasks.value.some(task => task === inputTask.value);
    if (taskExists) {
     
      alert("Você já adicionou essa tarefa");
    } else {
      tasks.value.push(inputTask.value);
      inputTask.value = "";
      addTaskLocalStorage();
      showPomoModal.value = false; 
    }
  }
};

const removeTask = (index) => {
  tasks.value.splice(index, 1);
  addTaskLocalStorage();
};

const addTaskLocalStorage = () => {
  localStorage.setItem("tasks", JSON.stringify(tasks.value));
};

const showPomoModal = ref(false);

const showPomoTask = () => {
  showPomoModal.value = !showPomoModal.value;
};

//quando clicado mostrar o componente Task, o component task é um input para adicionar tarefas, apos adcionar a task ela aparece no componente Pomodoro em ordem da mais recente para a mais antiga
</script>

<style scoped>
.task-container {
  font-family: sans-serif;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
h2 {
  font-size: 25px;
  color: #0f1729;
}
.add-task {
  width: 420px;

  height: 64px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  word-break: break-all;
}
.task {
  color: #0f1729;
  font-weight: 400;
  background-color: #f0f0f0;
  padding: 10px 10px;
  width: 400px;
  height: 64px;
}
.task-p {
  font-size: 18px;
  font-weight: 600;
  padding-left: 15px;
}
.task {
  border-radius: 10px;
}

.btn-show-task {
  
  font-weight: bold;
  background-color: #0f1729;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}
.btn-add-task {
  height: 100%;
  padding: 0 20px;
  background-color: #0f1729;
  color: white;
  border: none;
  cursor: pointer;

  border-radius: 5px;
}
.show-task {
  width: 400px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.btn-add-task:disabled {
  background-color: #f0f0f0;
  color: #0f1729;
  font-weight: 700;
  cursor: not-allowed;
}
.input-task {
  padding: 0;

  border: 0.5px solid #0f1729;
  font-weight: 700;
  font-size: 16px;
  /*padding: 5px 10px;*/
  height: 64px;
  background-color: #f0f0f0;
  border-radius: 10px;
  padding-left: 20px;
}
.input-task {
  outline-color: red;
}

.input-task:focus {
  outline: none;
}
.input-task::placeholder {
  padding: 10px 5px;
  color: #0f1729;
}
.btn-remove {
  background-color: transparent;
  border: none;
  cursor: pointer;
}
@media screen and (min-width: 767px) and (max-width: 1023px) {

h2 {
  font-size: 30px;
}
.show-task {
  width: 400px;
}
.btn-show-task{
  padding: 10px 30px;
}
.task {
  width: 380px;
}
.add-task{
  width: 400px;

}
}

@media screen and (min-width: 320px) and (max-width: 767px) {
  .task {
    width: 300px;
  }
  .input-task {
    width: 180px;
  }
  
.show-task {
  width: 300px;
}

.add-task{
  width: 320px;

}
}

@keyframes abrir {
  0% {
    opacity: 0;
    transform: scale(0.5);
    background-color: red;
  }
  50% {
    opacity: 1;
  }
  100% {
    transform: scale(1);
  }
}
</style>
