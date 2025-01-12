<template>
    <li>
      <input type="checkbox" v-model="todo.completed" />
      <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
      <button @click="$emit('remove')">Delete</button>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      todo: Object,
    },
  };
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  </style>
  