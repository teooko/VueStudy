<script setup>
import { onMounted, reactive, ref } from 'vue';
import Task from './Task.vue';
const tasks = ref([{name: "default task", done: true}]);
const newTask = reactive({name: "new Task", done: false});
const addTask = (taskName, isDone) => {
  tasks.value = [...tasks.value, {...newTask}];
}
const removeTask = (taskIndex) => {
  tasks.value = tasks.value.filter((task, index) => index !== taskIndex);
}
</script>

<template>
  <div class="task-list">
    <form class="form">
      <label for="name">Name:
        <input type="text" id="name" v-model="newTask.name"/>
      </label>
      <label for="done">Done
        <input type="checkbox" id="done"  v-model="newTask.done">
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
    width: 500px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 100px;
  }
</style>
