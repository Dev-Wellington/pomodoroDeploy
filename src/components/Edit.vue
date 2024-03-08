<template>
    <div>
        <button @click="editTimerModal"><img src="../assets/gear.svg" alt="Engrenagem de configuração"></button>



        <div class="cd pomeditTimerModal">
            <h2>Alterar tempos</h2>

            <label>
                Tempo do Pomodoro:
                <input type="number" v-model="newPomodoroTime" min="1">
            </label>

            <label>
                Tempo da pausa:
                <input type="number" v-model="newShortBreakTime" min="1">
            </label>

            <label>
                Tempo da pausa longa:
                <input type="number" v-model="newLongBreakTime" min="1">
            </label>

            <button @click="updateTimes" class="updateBtn">Atualizar tempos</button>
            <button @click="showModal = false" class="closeBtn">Fechar</button>
        </div>
    </div>

   
</template>

<script setup>

</script>

<style scoped>
button {
    background-color:transparent;
    border: none;
    cursor: pointer;
}
.editTimerModal{
    font-family: sans-serif;
}

.editTimerModal {
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   gap: 15px;
}
.updateBtn , .closeBtn{
    padding: 10px 20px;
    border-radius: 5px;
    border: none;
    color: #fff;
    cursor: pointer;
}
.updateBtn{
    background-color: green;
}
.closeBtn{
    background-color: red;
}
label{
    display: flex;
    flex-direction: column;
    gap: 5px;

}
label > input{
    padding: 10px;
    border-radius: 5px;
    border: none;

}

</style>