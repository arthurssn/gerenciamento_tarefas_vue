<template>
    <div class="card">
        <ControleTarefas @tarefaFinalizada="atualizarLista" :p_tarefa="tarefa" ref="controleTarefas"></ControleTarefas>
        <hr>
        <div v-if="tarefas.length > 0">
            <div class="lista-cabecalho">
                <h3>Lista de Tarefas</h3>
            </div>
            <div v-for="(tarefa, index) in tarefas" :key="index">
                <div class="tarefa-card">
                    <ListaTarefas :tarefa="tarefa" :index="index" @editarTarefa="atualizarTarefa"
                              @exlcuirTarefa="excluirTarefa" @iniciarNovamente="reiniciarTarefa">
                    </ListaTarefas>
                </div>
            </div>
        </div>
        <div v-else style="text-align: center">
            <div class="tarefa-card">
                Nenhuma tarefa concluída
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent } from 'vue';
import ControleTarefas from './ControleTarefas.vue';
import ListaTarefas from './ListaTarefas.vue';
export default defineComponent({
    data() {
        return {
            tarefas: [] as ITarefa[],
            tarefa: {
                duracaoEmSegundos: 0,
                descricao_tarefa: ''
            } as ITarefa
        }
    },
    components: {
        ControleTarefas,
        ListaTarefas
    },
    methods: {
        atualizarLista(tarefa: ITarefa) {
            this.tarefas.unshift(tarefa)
        },
        atualizarTarefa(descricao: string, index: number) {
            this.tarefas[index].descricao_tarefa = descricao;
        },
        excluirTarefa(index: number) {
            this.tarefas.splice(index, 1);
        },
        reiniciarTarefa(tarefa: ITarefa) {
            this.tarefa = tarefa;
            ((this.$refs.controleTarefas) as typeof ControleTarefas).iniciar();
        }
    },
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