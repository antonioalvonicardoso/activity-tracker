<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">{{task.description}}</div>
            <div class="column">
                <ActivityStopwatch :timeInSeconds="task.durationInSeconds"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import ActivityStopwatch from './ActivityStopwatch.vue'
import ITask from '@/interfaces/ITask';

export default defineComponent({
    name: 'ActivityTask',
    props:{
        task: { type: Object as PropType<ITask>, required: true},
    },
    components: {
    ActivityStopwatch
  }
});
</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>