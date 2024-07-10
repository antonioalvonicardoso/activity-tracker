<template>
  <main class="columns is-gaples is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <ActivityForm @saveTask="saveTask" />
      <div class="list">
        <ActivityBox v-if="listIsEmpty"> Você não esta muito produtivo hoje! </ActivityBox>
        <ActivityTask v-else v-for="(task, index) in tasks" :key="index" :task="task" />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import ActivityForm from './components/ActivityForm.vue';
import ActivityTask from './components/ActivityTask.vue';
import ITask from './interfaces/ITask';
import ActivityBox from './components/ActivityBox.vue';

export default defineComponent({
  name: 'App',
  data() {
    return {
      tasks: [] as ITask[]
    }
  },
  components: {
    SideBar,
    ActivityForm,
    ActivityTask,
    ActivityBox
  },
  computed: {
    listIsEmpty() : boolean{
      return this.tasks.length === 0;
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task);
    }
  }
});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
