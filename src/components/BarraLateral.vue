<template>
    <div class="coluna">
        <h1>Gerenciamento de Tarefas</h1>
        <img src="../../public/Gerenciamento-de-Tempo.png" alt="Gerenciamento de Tempo" class="img-logo">
        <button class="btn btn-coluna">
            Modo escurro
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({

})
</script>

<style>
.coluna {
    width: 18vw;
    height: 100vh;
    background-color: rgb(0, 37, 105);
    display: flex;
    flex-direction: column;
    color: #fff;
    text-align: center;
}

.img_logo {
    border-radius: 10px;
    width: 70%;

    position: relative;
    top: 10%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.btn-coluna {
    position: relative;
    top: 60%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 10px;
    border-radius: 10px;
    border: none;
    width: 50%;

    font-weight: bolder;
}
</style>