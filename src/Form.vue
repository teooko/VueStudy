<script setup>
    const model = defineProps(['newTask']);
    const emit = defineEmits(['addTask']);
</script>

<template>
    <form class="form">
      <label for="name">Name:
        <input type="text" id="name" v-model="model.newTask.name"/>
      </label>
      <label for="done">Done
        <input type="checkbox" id="done"  v-model="model.newTask.done">
      </label>
      <button @click.prevent="$emit('addTask')">addTask</button>
    </form>
</template>

<style scoped>
  .form {
    width: 522px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 100px;
  }
</style>