<script setup lang="ts">
import { onMounted, ref } from 'vue';

let userName = 'Boiko Dmitry';

let newUserName = ref('Vlad Sokolov');

const users = ['Dima', 'Vlad', 'Artur'];

function changeName(event: Event) {
  const target = event.target as HTMLButtonElement;
  newUserName.value += '10';
  target.disabled = true;
}

let h2 = ref();
</script>

<template>
  <h1>Welcome home, {{ userName }}</h1>

  <h2>User List</h2>
  <ul>
    <li v-for="user in users" :key="user">{{ user.toUpperCase() }}</li>
  </ul>

  <h2 ref="h2">I'm {{ newUserName }}</h2>

  <button @click="changeName">Change Name</button>
</template>
