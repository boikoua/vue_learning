<script setup>
defineProps({
  id: Number,
  name: String,
  salary: Number,
  age: Number,
  languages: {
    type: Array,
  },
});

defineEmits(['delete']);
</script>

<template>
  <h2>Hello from Employee</h2>
  <p>Name: {{ name }}</p>
  <p>Salary: {{ salary }}$</p>
  <p>Age: {{ age }}</p>
  <ul>
    <li v-for="(lang, index) in languages" :key="index">{{ lang }}</li>
  </ul>

  <div>
    <button @click="$emit('delete', id)">Remove user</button>
  </div>
  <hr />
</template>

<style scoped></style>
