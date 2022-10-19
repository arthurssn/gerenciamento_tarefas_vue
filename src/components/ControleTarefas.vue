<template>
    <div>
        <div class="form">
            <div class="row">
                <input type="text" class="form-input col-7" placeholder="Nova tarefa" v-model="descricao_tarefa">
                <button class="btn form-btn" type="button" @click="iniciar" v-if="!tempo_rodando">
                    <i class="fas fa-play"></i>
                </button>
                <button class="btn form-btn" type="button" @click="pausar" v-else>
                    <i class="fas fa-pause"></i>
                </button>
                <button class="btn form-btn" type="button" @click="finalizar">
                    <i class="fas fa-stop"></i>
                </button>
                <CronometroTarefa :tempoEmSegundos="10"></CronometroTarefa>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';

export default defineComponent({
    data() {
        return {
            descricao_tarefa: '',
            tempo_rodando: false,
        }
    },
    components: {
        CronometroTarefa
    },
    methods: {
        iniciar(): void {
            console.log('oi')
        },

        pausar(): void {
            console.log('oi')
        },

        finalizar(): void {
            console.log('oi')
        }
    },
})
</script>