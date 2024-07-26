<template>
    <section class="display">
        <strong>{{ elapsedTime }}</strong> <!--Acessa como se fosse uma propriedade-->
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'ActivityStopwatch',
    props: {
        timeInSeconds: {type: Number, default: 0}
    },
    computed: {
        elapsedTime(): string {
            return new Date(this.timeInSeconds * 1000).toISOString().substr(11, 8);
        }
    },
});
</script>

<style scoped>
.display{
    background-color: var(--bg-primary);
    color: var(--text-primary);
}
</style>