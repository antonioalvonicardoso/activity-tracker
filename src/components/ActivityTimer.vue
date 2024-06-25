<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <ActivityStopwatch :timeInSeconds="timeInSeconds" />
        <TimerButton @click="start" icon="fas fa-play" text="play" :disabled="stopwatchRunning" />
        <TimerButton @click="finish" icon="fas fa-stop" text="stop" :disabled="!stopwatchRunning" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ActivityStopwatch from './ActivityStopwatch.vue';
import TimerButton from './TimerButton.vue';

export default defineComponent({
    name: 'ActivityTimer',
    data() {
        return {
            timeInSeconds: 0,
            stopwatch: 0,
            stopwatchRunning: false,
        }
    },
    emits: ['atTheEndOfTheTimer'],
    components: {
        ActivityStopwatch, TimerButton
    },
    methods: {
        start() {
            this.stopwatchRunning = true;
            this.stopwatch = setInterval(() => { //Guardar a referencia do setInterval
                this.timeInSeconds++;
                console.log(this.timeInSeconds);
            }, 1000); // 1 seg == 1000 ms
        },

        finish() {
            this.stopwatchRunning = false;
            clearInterval(this.stopwatch);
            this.$emit('atTheEndOfTheTimer', this.timeInSeconds);
            this.timeInSeconds = 0;
        }
    },
});
</script>