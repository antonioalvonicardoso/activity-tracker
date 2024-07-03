<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                Descrição Tarefa
            </div>
            <div class="column">
                <ActivityStopwatch :timeInSeconds="15"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ActivityStopwatch from './ActivityStopwatch.vue'

export default defineComponent({
    name: 'ActivityTask',
    components: {
    ActivityStopwatch
  }
});
</script>