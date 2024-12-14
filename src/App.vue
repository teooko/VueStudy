<script setup>
import { onMounted, ref } from 'vue';
import Task from './Task.vue';
const tasks = ref([{name: "default task", done: true}]);

const addTask = (taskName, isDone) => {
  tasks.value = [...tasks.value, {name: taskName, done: isDone}];
}
const removeTask = (taskIndex) => {
  tasks.value = tasks.value.filter((task, index) => index !== taskIndex);
}
</script>

<template>
  <div>
    <div v-for="(task, index) in tasks" :key="index">
      <Task :name="task.name" :done="task.done" @remove="removeTask(index)"/>
    </div>
    <button @click="addTask(`new task`, false)">addTask</button>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
