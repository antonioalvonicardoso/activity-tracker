<!-- Formulario.vue -->

<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?"  v-model="description"/>
            </div>
            <div class="column">
                <ActivityTimer @at-the-end-of-the-timer="finishTask"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ActivityTimer from './ActivityTimer.vue';

export default defineComponent({
    name: 'ActivityForm',
    emits: ['saveTask'],
    data() {
        return{
            description: '',
        }
    },
    components: {
        ActivityTimer
    },
    methods: {
        finishTask(timeInSeconds: number) : void{
            this.$emit('saveTask', {
                durationInSeconds: timeInSeconds,
                description: this.description
            });
            this.description = '';
        }
    }
});
</script>