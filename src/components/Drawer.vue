<script setup>
import { inject } from 'vue';
import CartList from './CartList.vue';
import DrawerHead from './DrawerHead.vue';

defineProps({
  items: Array,
});

const totalSum = inject('totalSum');
const taxSum = inject('taxSum');
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 bg-opacity-70">
    <div class="fixed right-0 top-0 bg-white w-screen md:w-96 h-full z-20 p-5 flex flex-col">
      <DrawerHead />

      <div class="flex-1 overflow-y-auto">
        <CartList />
      </div>

      <div class="flex flex-col gap-2 mt-4">
        <div class="flex gap-2">
          <span>Всього:</span>
          <div class="relative bottom-1 flex-1 border-b-2 border-dotted"></div>
          <b>{{ totalSum }} ₴</b>
        </div>

        <div class="flex gap-2 mb-4">
          <span>ПДВ 25%:</span>
          <div class="relative bottom-1 flex-1 border-b-2 border-dotted"></div>
          <b>{{ taxSum }} ₴</b>
        </div>

        <button
          class="bg-lime-500 w-full rounded-xl py-3 text-white transition hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-400"
        >
          Замовити
        </button>
      </div>
    </div>
  </div>
</template>
