<template>
    <div>
        <div class="form">
            <div class="row">
                <input type="text" class="form-input col-7" placeholder="Nova tarefa" v-model="tarefa.descricao_tarefa"
                          :disabled="input_disabled">
                <CronometroTarefa :tempoEmSegundos="tarefa.duracaoEmSegundos"></CronometroTarefa>
                <button class="btn form-btn" type="button" @click="iniciar" v-if="!tempo_rodando">
                    <i class="fas fa-play"></i>
                </button>
                <button class="btn form-btn" type="button" @click="pausar" v-else>
                    <i class="fas fa-pause"></i>
                </button>
                <button class="btn form-btn" type="button" @click="finalizar">
                    <i class="fas fa-stop"></i>
                </button>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';
export default defineComponent({
    data() {
        return {
            tarefa: this.p_tarefa,
            tempo_rodando: false,
            cronometro_id: 0,
            input_disabled: false,
            class_cronometro: '',
        }
    },
    props: {
        p_tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    },
    components: {
        CronometroTarefa
    },
    emits: ['tarefaFinalizada'],
    methods: {
        iniciar(): void {
            this.tempo_rodando = true;
            this.class_cronometro = 'cronometro_rodando';
            this.input_disabled = true;
            this.cronometro_id = setInterval(() => {
                this.tarefa.duracaoEmSegundos++;
            }, 1000)
        },

        pausar(): void {
            this.class_cronometro = '';
            this.tempo_rodando = false;
            this.input_disabled = false;
            clearInterval(this.cronometro_id);
        },

        finalizar(): void {
            this.input_disabled = false;
            this.$emit('tarefaFinalizada', {
                descricao_tarefa: this.tarefa.descricao_tarefa,
                duracaoEmSegundos: this.tarefa.duracaoEmSegundos
            })
            this.pausar();
            this.tarefa.duracaoEmSegundos = 0;
            this.tarefa.descricao_tarefa = '';
        }
    },
    watch: {
        p_tarefa() {
            this.tarefa = this.p_tarefa;
        }
    }
})
</script>
<style>
.cronometro-rodando {
    color: rgb(255, 255, 255);
}
</style>