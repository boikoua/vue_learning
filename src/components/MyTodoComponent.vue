<script setup>
import { reactive, ref } from 'vue';

const textForNewTodo = ref('');

const todos = reactive(
  localStorage.getItem('todos')
    ? JSON.parse(localStorage.getItem('todos'))
    : [
        {
          id: 1,
          text: 'Drink coffee',
        },
        {
          id: 2,
          text: 'Meet with friends',
        },
        {
          id: 3,
          text: 'Cook the dinner',
        },
        {
          id: 4,
          text: 'Go to bed',
        },
      ]
);

const addNewTodo = (newTodo) => {
  if (!newTodo.trim()) return;

  todos.push({ id: todos.length + 1, text: newTodo });
  textForNewTodo.value = '';

  localStorage.setItem('todos', JSON.stringify(todos));
};

const deleteTodo = (id) => {
  const index = todos.findIndex((todo) => todo.id === id);

  if (index !== -1) {
    todos.splice(index, 1);
  }

  localStorage.setItem('todos', JSON.stringify(todos));
};
</script>

<template>
  <div class="container">
    <ul class="task-list">
      <li class="task-item" v-for="todo of todos" :key="todo.id">
        <p>{{ todo.text }}</p>
        <button class="delete-btn" @click="deleteTodo(todo.id)">Delete</button>
      </li>
    </ul>

    <form class="add-task-form" @submit.prevent="addNewTodo(textForNewTodo)">
      <input v-model="textForNewTodo" type="text" placeholder="New todo..." />
      <button type="submit">Add new todo</button>
    </form>
  </div>
</template>

<style scoped>
.container {
  width: 400px;
  margin: 100px auto;
  padding: 20px;
  background-color: white;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  text-align: center;
}

.task-list {
  list-style: none;
  padding: 0;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 10px;
  margin-bottom: 10px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.task-item p {
  font-weight: bold;
  color: black;
}

.add-task-form {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

.add-task-form input {
  width: 300px;
  padding: 10px;
  font-size: 16px;
  border-radius: 8px;
  border: 1px solid #ccc;
}

.add-task-form button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.add-task-form button:hover {
  background-color: #0056b3;
}

.delete-btn {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.delete-btn:hover {
  background-color: #c82333;
}
</style>
