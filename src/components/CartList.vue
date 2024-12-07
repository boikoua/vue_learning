<script setup>
import { inject } from 'vue';
import CartItem from './CartItem.vue';

const items = inject('items');

const itemsInCart = items.value.filter((item) => item.isAdded);
</script>

<template>
  <div class="flex flex-col gap-4 mb-4">
    <CartItem v-for="item in itemsInCart" :key="item.id" :item="item" />
  </div>
</template>
