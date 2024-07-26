<template>
  <main class="columns is-gaples is-multiline" :class="{'dark-mode': darkModeActive}">
    <div class="column is-one-quarter">
      <SideBar @changedTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
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
      tasks: [] as ITask[],
      darkModeActive: false,
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
    },

    changeTheme(darkMode: boolean){
      this.darkModeActive = darkMode;
    }
  }
});
</script>

<style>
main {
  --bg-primary: #fff;
  --text-primary: #000;
}

main.dark-mode{
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}

.content{
  background-color: var(--bg-primary)
}

.list {
  padding: 1.25rem;
}
</style>
