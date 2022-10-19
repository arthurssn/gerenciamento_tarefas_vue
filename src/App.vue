<template>
  <main :class="tema">
    <div class="conteudo">
      <BarraLateral @alterarTema="alterarTema"></BarraLateral>
      <JanelasTarefa></JanelasTarefa>
    </div>
  </main>
</template>

<script lang="ts">
import BarraLateral from './components/BarraLateral.vue';
import JanelasTarefa from './components/JanelaTarefas.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    JanelasTarefa
  },
  data() {
    return {
      tema: '',
      modo_escuro: false
    }
  },
  methods: {
    alterarTema(modo_escuro: boolean) {
      modo_escuro ? this.tema = 'modo-escuro' : this.tema = ''
    }
  },
});
</script>