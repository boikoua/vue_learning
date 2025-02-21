<script setup>
import { ref } from 'vue';

const items = ref(['car']);
const inputValue = ref('');

function addNewItem() {
  if (inputValue.value) {
    items.value.unshift(inputValue.value);
  }
}

function removeItem(index) {
  items.value = items.value.filter((_, i) => i !== index);
}

const users = ref([
  {
    id: 1,
    name: 'name1',
    surn: 'surn1',
    isEdit: false,
  },
  {
    id: 2,
    name: 'name2',
    surn: 'surn2',
    isEdit: false,
  },
  {
    id: 3,
    name: 'name3',
    surn: 'surn3',
    isEdit: false,
  },
]);

function editFunc(user) {
  user.isEdit = true;
}

function saveFunc(user) {
  user.isEdit = false;
}
</script>

<template>
  <ul>
    <li v-for="user in users" :key="user.id">
      <template v-if="!user.isEdit">
        {{ user.name }}
        {{ user.surn }}

        <button @click="editFunc(user)">edit</button>
      </template>

      <template v-else>
        <input type="text" v-model="user.name" />
        <input type="text" v-model="user.surn" />

        <button @click="saveFunc(user)">save</button>
      </template>
    </li>
  </ul>
  <hr />
  <input type="text" v-model="inputValue" />
  <br />
  <br />
  <button @click="addNewItem">Add a new item</button>

  <ul v-show="items.length">
    <li v-for="(item, index) of items" :key="index">
      {{ item }} <button @click="removeItem(index)">Remove Item</button>
    </li>
  </ul>
</template>

<style scoped></style>
