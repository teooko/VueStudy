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
    <form class="form">
      <label for="name">Name:
        <input type="text" id="name"/>
      </label>
      <label for="done">Done
        <input type="checkbox" id="done">
      </label>
      <button @click.prevent="addTask(`new task`, false)">addTask</button>
    </form>
    <div v-for="(task, index) in tasks" :key="index">
      <Task :name="task.name" :done="task.done" @remove="removeTask(index)"/>
    </div>
  </div>
</template>

<style scoped>
  .task-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
    height: 100vh;
  }

  .form {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 100px;
  }
</style>
