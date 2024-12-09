<script setup>
import { computed, inject } from 'vue';
import CartItem from './CartItem.vue';

const items = inject('items');

let itemsInCart = computed(() => items.value.filter((item) => item.isAdded));

// Функция удаления товара из конзины
const deleteFromCart = (id) => {
  const findIndex = items.value.findIndex((item) => item.id === id);

  if (findIndex !== -1) {
    items.value[findIndex].isAdded = false;
  }

  localStorage.setItem('items', JSON.stringify(items.value));
};
</script>

<template>
  <div class="flex flex-col gap-4 mb-4" v-auto-animate>
    <CartItem
      v-for="item in itemsInCart"
      :key="item.id"
      :item="item"
      :deleteFromCart="deleteFromCart"
    />
  </div>
</template>
