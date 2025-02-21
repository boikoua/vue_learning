<script setup>
const items = ['John', 'David', 'Eddy', 'Carol', 'Katie'];

const users = {
  user1: '100$',
  user2: '200$',
  user3: '300$',
};

const products = [
  {
    name: 'product1',
    price: 100,
    quantity: 5,
  },
  {
    name: 'product2',
    price: 200,
    quantity: 4,
  },
  {
    name: 'product3',
    price: 300,
    quantity: 3,
  },
];
</script>

<template>
  <ul>
    <li v-for="(item, index) in items" :key="index">{{ item }}</li>
  </ul>

  <ul>
    <li v-for="(user, key, index) in users" :key="key">{{ `${key} - ${user} - ${index + 1}` }}</li>
  </ul>

  <ul>
    <template v-for="(item, index) in items" :key="index">
      <li>{{ item }}</li>
      <li class="divider"></li>
    </template>
  </ul>

  <table>
    <caption>
      Products
    </caption>
    <tr>
      <th>index</th>
      <th>name</th>
      <th>price</th>
      <th>quantity</th>
    </tr>

    <tr v-for="(prod, index) in products" :key="index">
      <td>{{ index }}</td>
      <td>{{ prod.name }}</td>
      <td>{{ prod.price }}</td>
      <td>{{ prod.quantity }}</td>
    </tr>
  </table>

  <ul>
    <template v-for="item in items" :key="item">
      <li v-if="item.length < 5">{{ item }}</li>
    </template>
  </ul>
</template>

<style scoped>
.divider {
  display: block;
  height: 1px;
  width: 100%;
  background-color: gray;
}

table {
  border-collapse: collapse;
}

table,
th,
td {
  border: 2px solid gray;
}

th,
td {
  padding: 10px;
  text-align: center;
}
</style>
