<template>
  <main class="columns is-gaples is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <ActivityForm />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import ActivityForm from './components/ActivityForm.vue';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    ActivityForm
  }
});
</script>

<style></style>
