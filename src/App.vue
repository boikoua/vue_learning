<script setup>
import { ref } from 'vue';

const items = ref(['hello', 'my', 'car']);

function addNewItem() {
  items.value.push('i am a new item');
}

function deleteFirstItem() {
  items.value.shift();
}

function sortAllItems() {
  items.value.sort((a, b) => a.localeCompare(b));
}

function reverseItems() {
  items.value.reverse();
}
</script>

<template>
  <button @click="addNewItem">add a new item</button>
  <br />
  <br />
  <button @click="deleteFirstItem">delete the first item</button>
  <br />
  <br />
  <button @click="sortAllItems">sort all items</button>
  <br />
  <br />
  <button @click="reverseItems">reverse all items</button>

  <ul>
    <li v-for="(item, index) in items" :key="index">{{ item }}</li>
  </ul>
</template>

<style scoped></style>
