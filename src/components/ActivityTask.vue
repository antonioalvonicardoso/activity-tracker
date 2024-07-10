<template>
    <ActivityBox>
        <div class="columns">
            <div class="column is-7">{{task.description || 'Tarefa sem descrição'}}</div>
            <div class="column">
                <ActivityStopwatch :timeInSeconds="task.durationInSeconds"/>
            </div>
        </div>
    </ActivityBox>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import ActivityStopwatch from './ActivityStopwatch.vue';
import ActivityBox from './ActivityBox.vue';
import ITask from '@/interfaces/ITask';

export default defineComponent({
    name: 'ActivityTask',
    props:{
        task: { type: Object as PropType<ITask>, required: true},
    },
    components: {
    ActivityStopwatch, ActivityBox
  }
});
</script>