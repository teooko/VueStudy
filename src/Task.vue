<script setup>
    import { defineProps, defineEmits } from 'vue';
    const props = defineProps(['name', 'done', 'removeTak']);
    const emit = defineEmits(['remove']);
</script>   

<template>
    <div class="task">
        {{ props.name }}
      <div v-if="props.done">DONE</div>
      <button @click="$emit('remove')">remove task</button>
    </div>
</template>

<style scoped>
    .task {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        padding: 10px;
        border: 1px solid black;
        border-radius: 5px;
        width: 500px;
    }
</style>