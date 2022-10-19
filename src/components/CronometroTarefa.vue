<template>
    <div>
        {{tempoDecorrido}}
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    props: {
        tempoEmSegundos: {
            type: Number,
            required: true
        }
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(1000 * this.tempoEmSegundos).toISOString().substring(11, 19)
        }
    }
})
</script>