<script setup>
import { onMounted, reactive, ref } from 'vue';
import Task from './Task.vue';
import CustomForm from './Form.vue';

const tasks = ref([{name: "default task", done: true}]);
const newTask = reactive({name: "new Task", done: false});
const addTask = () => {
  tasks.value = [...tasks.value, {...newTask}];
}
const removeTask = (taskIndex) => {
  tasks.value = tasks.value.filter((task, index) => index !== taskIndex);
}
</script>

<template>
  <div class="task-list">
    <CustomForm :newTask="newTask" @addTask="addTask" />
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
</style>
