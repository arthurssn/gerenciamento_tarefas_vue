<template>
  <main :class="tema">
    <BarraLateral></BarraLateral>
    <JanelasTarefa></JanelasTarefa>
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
      tema: ''
    }
  },
});
</script>