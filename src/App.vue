<script setup>
import { ref } from 'vue';
import TheEmployee from './components/TheEmployee.vue';

const users = ref([
  {
    id: 1,
    name: 'David',
    salary: 600,
    age: 30,
    langs: ['html', 'css', 'js'],
  },
  {
    id: 2,
    name: 'John',
    salary: 1000,
    age: 40,
    langs: ['html', 'css', 'js', 'ts'],
  },
  {
    id: 3,
    name: 'Christi',
    salary: 1500,
    age: 50,
    langs: ['html', 'css', 'js', 'c#'],
  },
]);

function removeUser(id) {
  users.value = users.value.filter((user) => user.id !== id);
}
</script>

<template>
  <TheEmployee
    v-for="user in users"
    :key="user.id"
    :id="user.id"
    :name="user.name"
    :salary="user.salary"
    :age="user.age"
    :languages="user.langs"
    @delete="removeUser"
  />
</template>

<style scoped></style>
