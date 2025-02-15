<script setup>
import { ref } from 'vue';

let id = 0;

const newTodo = ref('');
const todos = ref([
  { id: id++, text: 'Изучить HTML' },
  { id: id++, text: 'Изучить JavaScript' },
  { id: id++, text: 'Изучить Vue' },
]);

function addTodo() {
  todos.value = [...todos.value, { id: id++, text: newTodo.value }];
  newTodo.value = '';
}

function removeTodo(todo) {
  todos.value = todos.value.filter((item) => item.id !== todo.id);
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo" />
    <button>Добавить задачу</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>
