<template>
    <div class="coluna">
        <h1>Gerenciamento de Tarefas</h1>
        <img src="../../public/Gerenciamento-de-Tempo.png" alt="Gerenciamento de Tempo" class="img_logo">
        <button class="btn btn-coluna" @click="alterarTema">
            <div>
                {{txt_btn}}
                <i class="fas fa-moon" v-if="!modo_escuro"></i>
                <i class="far fa-moon" v-else></i>
            </div>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    emits: ['alterarTema'],
    data() {
        return {
            modo_escuro: false,
        }
    },
    methods: {
        alterarTema() {
            this.modo_escuro = !this.modo_escuro;
            this.$emit('alterarTema', this.modo_escuro);
        }
    },
    computed: {
        txt_btn() {
            return this.modo_escuro ? 'Modo Claro' : 'Modo Escuro'
        }
    }
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