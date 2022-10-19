<template>
    <div class="row">
        <div class="lista-item col-7">
            <span v-if="!modo_edicao">{{ tarefa.descricao_tarefa || 'Tarefa sem descrição'}}</span>
            <div v-else>
                <input type="text" class="form-input" v-model="tarefa_edit">
                <button class="btn form-btn" @click="salvarEdicao">
                    <i class="fas fa-check"></i>
                    <i class="fas fa-file-check"></i>
                </button>
            </div>
        </div>
        <div class="cronometro">
            <CronometroTarefa :tempoEmSegundos="tarefa.duracaoEmSegundos"></CronometroTarefa>
        </div>
        <button class="btn form-btn" type="button" @click="iniciarNovamente">
            <i class="fas fa-play"></i>
        </button>
        <button class="btn form-btn" @click="editarTarefa">
            <i class="fas fa-pen"></i>
        </button>
        <button class="btn form-btn" type="button" @click="excluirTarefa">
            <i class="fas fa-times"></i>
        </button>
    </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue'
import CronometroTarefa from './CronometroTarefa.vue';
export default defineComponent({
    data() {
        return {
            modo_edicao: false,
            tarefa_edit: this.tarefa.descricao_tarefa
        }
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        },
        index: {
            type: Number,
            required: true
        }
    },
    components: {
        CronometroTarefa
    },
    emits: ['iniciarNovamente', 'editarTarefa', 'exlcuirTarefa'],
    methods: {
        salvarEdicao() {
            this.$emit('editarTarefa', this.tarefa_edit, this.index)
            this.modo_edicao = false;
        },
        iniciarNovamente() {
            this.$emit('iniciarNovamente', this.tarefa);
            this.excluirTarefa()
        },
        editarTarefa() {
            this.modo_edicao = !this.modo_edicao;
        },
        excluirTarefa() {
            this.$emit('exlcuirTarefa', this.index);
        }
    },
    watch: {
        tarefa() {
            this.tarefa_edit = this.tarefa.descricao_tarefa
        }
    }
})
</script>

<style>
.lista {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.lista-cabecalho {
    color: #fff;
    text-align: center;
}
</style>