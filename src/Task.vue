<script setup>
    import { defineProps, defineEmits } from 'vue';
    const props = defineProps(['name', 'done', 'removeTak']);
    const emit = defineEmits(['remove']);
</script>   

<template>
    <div>
        {{ props.name }}
      <div v-if="props.done">DONE</div>
      <button @click="$emit('remove')">remove task</button>
    </div>
</template>