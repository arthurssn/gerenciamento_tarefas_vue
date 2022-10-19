<template>
    <div class="card">
        <ControleTarefas></ControleTarefas>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ControleTarefas from './ControleTarefas.vue';
export default defineComponent({
    components: {
        ControleTarefas,
    }
})
</script>

<style>
.card {
    background-color: rgb(44, 117, 252);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0.9;
    padding: 10px;
    border-radius: 10px;

    width: 35vw;
    height: 70vh;
}


.tarefa-card {
    background-color: rgb(0, 69, 197);
    padding: 10px;
    border-radius: 10px;
    margin-bottom: 10px;

    -webkit-box-shadow: 5px 5px 37px 10px rgba(0, 0, 0, 0.19);
    box-shadow: 5px 5px 37px 10px rgba(0, 0, 0, 0.19);

    color: #fff;
}
</style>