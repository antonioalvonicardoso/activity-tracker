<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <ActivityStopwatch :timeInSeconds="timeInSeconds" />
        <button class="button" @click="start()" :disabled="stopwatchRunning">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="finish()" :disabled="!stopwatchRunning">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ActivityStopwatch from './ActivityStopwatch.vue';

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
        ActivityStopwatch
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