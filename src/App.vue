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
  <div class="task-list">
    <div v-for="(task, index) in tasks" :key="index">
      <Task :name="task.name" :done="task.done" @remove="removeTask(index)"/>
    </div>
    <button @click="addTask(`new task`, false)">addTask</button>
  </div>
</template>

<style scoped>
  .task-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
    height: 100vh;
  }
</style>
